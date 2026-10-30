## Overview
Phishing is a trick where criminals use fake links to steal passwords or payment details. This Python tool reads a URL as plain text and points out visible warning signs. It never opens the link.

## Features
- Detects an @ symbol in the URL
- Flags unusually long URLs (over 100 characters)
- Flags IP-address hostnames
- Flags many hostname segments (5 or more)
- Flags punycode-style hostnames (xn--)
- Flags the HTTP scheme
- Loop with quit command: check many URLs without restarting
- "Review carefully" summary with a warning count
- Handles malformed input without crashing

## Requirements
Python 3.10 or later. No extra packages.

## How to Run
Windows: python phishing_checker.py
Mac/Linux: python3 phishing_checker.py

Type a sample URL and press Enter. Type q to quit.

## Example Output
EWB Phishing URL Awareness Checker
Text checks only - this program does not open URLs.

Enter a sample URL (or type q to quit): http://192.0.2.10/account

Result:
- Uses an IP address instead of a familiar domain.
- Uses HTTP. HTTPS alone does not prove trust.

REVIEW CAREFULLY: 2 warning sign(s) found.
Never enter passwords from unexpected links.

## Testing
| # | Input | Expected | Actual | Result |
|---|-------|----------|--------|--------|
| 1 | https://www.example.com/login | No warning signs | No listed warning signs found | PASS |
| 2 | http://192.0.2.10/account | IP address + HTTP | IP address and HTTP flagged | PASS |
| 3 | http://example.com@sample.invalid/login | @ symbol + HTTP | @ symbol and HTTP flagged | PASS |
| 4 | https://a.b.c.d.e.example.invalid/path | Many hostname segments | Many hostname segments flagged | PASS |
| 5 | https://xn--example.invalid/ | Punycode-style hostname | Punycode-style hostname flagged | PASS |

The full table is in tests/test_samples.md.

## Screenshots


![Sample run](screenshots/sample_run.png)




![Test results](screenshots/test_results.png)



## Improvements
1. Loop with quit - the program now keeps asking for URLs until the user types q, so I can test many URLs without restarting. I tested it by entering several URLs in a row and then quitting.
2. Review carefully summary - when real warnings are found, the program prints how many were found. I tested it with http://192.0.2.10/account, which shows 2 warnings.
3. Malformed input handling - typing http://[bad used to crash the program with a ValueError. I added try/except so it now prints a clear message instead. I tested it by typing http://[bad and then re-running all five sample tests.

## Limitations
This is an educational tool. It only reads URL text. It does not visit URLs, scan for malware or prove that a URL is safe. No warning signs found does NOT mean a URL is safe.

## Ethical Use
Use sample strings only. Do not collect credentials. Do not use this project to deceive anyone or to test websites without permission.

## Author
Ananya Singh,AI-POWERED CYBERSECURITY INTERNSHIP, EWB Courses