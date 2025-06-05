# Password Strength Analysis Report
## Objective
Evaluate multiple passwords of varying complexity using online password strength tools, identify what makes a password strong, and summarize findings related to security best practices.

## Tools Used
 - Online password checker: https://passwordmeter.com
 - Manual analysis and review


## Passwords Tested
<pre>
| Password            | Complexity Features                     | PasswordMeter Score | Feedback                                |
| ------------------- | --------------------------------------- | ------------------- | --------------------------------------- |
| `password123`       | lowercase + digits                      | 26% (Weak)          | Too short, common word, no symbols      |
| `P@ssw0rd!`         | Uppercase + lowercase + digits + symbol | 70% (Moderate)      | Better structure, but still predictable |
| `3x!T@9pL#v$Kz`     | Mixed case + symbols + digits           | 100% (Strong)       | Excellent length and complexity         |
| `MyCatIsFluffy2025` | Phrase + digits                         | 55% (Moderate)      | Good length but lacks symbol complexity |
| `!Qaz2WSx#Edc4RFv`  | Random + structured                     | 100% (Strong)       | High entropy, secure                    |
</pre>

![image](https://github.com/user-attachments/assets/beba636f-36f4-437a-bd80-e07f98b424a5)

![image](https://github.com/user-attachments/assets/e0ca522b-3fda-4082-b187-0f1ca32749f7)

# Observations
 - Short and simple passwords (e.g., password123) are highly insecure and easily cracked.
 - Common substitutions like @ for a (in P@ssw0rd) help a bit, but pattern-based passwords remain vulnerable.
 - Passwords with randomized structure, length >12, and use of symbols, digits, uppercase and lowercase letters score best.
 - Passphrases (e.g., MyCatIsFluffy2025) are easier to remember and can be strong if symbols are added.

#  Tips for Creating Strong Passwords
✔ Use at least 12–16 characters.
✔ Combine uppercase, lowercase, numbers, and symbols.
✔ Avoid dictionary words or common patterns.
✔ Don't reuse passwords across different accounts.
✔ Use a password manager to store complex passwords.
✔ Consider using random passphrases with special characters.


## Common Password Attacks
<pre>
| Attack Type             | Description                                                    |
| ----------------------- | -------------------------------------------------------------- |
| **Brute Force**         | Tries every possible combination; weak passwords fall quickly. |
| **Dictionary Attack**   | Uses lists of common passwords and variations.                 |
| **Phishing**            | Tricks users into revealing passwords.                         |
| **Keylogging**          | Captures what you type.                                        |
| **Credential Stuffing** | Tries leaked passwords on different accounts.                  |

</pre>

## How Complexity Affects Security
 - More entropy (randomness) means more combinations for an attacker to guess.
 - A 16-character password with mixed character types can take centuries to crack with brute force.
 - Even a moderately strong password is much better than a common or reused one.
