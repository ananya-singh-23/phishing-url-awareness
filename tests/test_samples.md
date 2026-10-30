# Test Results
Python version used: 3.14.6 | Operating system: Windows 11  | Date:30.10.2026
| # | Input | Expected result | Actual result | Pass/Fail |
|---|-------|-----------------|---------------|-----------|
| 1 | https://www.example.com/login | No listed warning signs | Pass |
| 2 | http://192.0.2.10/account | IP address + HTTP | Pass |
| 3 | http://example.com@sample.invalid/login | @ symbol + HTTP | Pass |
| 4 | https://a.b.c.d.e.example.invalid/path | Many hostname segments | Pass |
| 5 | https://xn--example.invalid/ | Punycode-style hostname | Pass |
## Notes
I thought in the earlier times checking URL was one of the difficult tasks but by doing  this it makes me feel easy and highly interesting and got to know that phishing checks can look at clues like @ symbols and IP addresses without opening the link.