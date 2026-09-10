# Career Connect - Auth Module Testing

Manual testing of the signup, OTP verification and login screens of Career Connect, a MERN job
portal. The app was run locally and every case was executed by hand in the browser.

**59 test cases | 58 executed | 10 defects | 82.8% pass rate**

| | Signup | OTP | Login | Total |
|---|---|---|---|---|
| Cases | 28 | 15 | 16 | **59** |
| Pass | 22 | 13 | 13 | **48** |
| Fail | 6 | 1 | 3 | **10** |
| Not executed | 0 | 1 | 0 | **1** |

## Defects

| ID | Test case | Summary | Severity |
|---|---|---|---|
| D-07 | TC_OTP_006 | No limit on wrong OTP attempts | **High** |
| D-09 | TC_LOGIN_012 | No limit on repeated wrong-password attempts | **High** |
| D-01 | TC_REG_007 | Full Name accepts digits | Medium |
| D-02 | TC_REG_013 | Mobile numbers starting with 97 are rejected | Medium |
| D-03 | TC_REG_018 | Full Name accepts unsupported symbols | Medium |
| D-04 | TC_REG_024 | Valid minimum-length password is rejected | Medium |
| D-05 | TC_REG_025 | Password without an uppercase letter is accepted | Medium |
| D-06 | TC_REG_028 | Valid non-Gmail addresses are rejected | Medium |
| D-08 | TC_LOGIN_009 | Uppercase form of a registered email is rejected | Medium |
| D-10 | TC_LOGIN_016 | Login messages reveal whether an email is registered | Medium |

## Main findings

**Three security issues that combine.** Login returns a different message for an unregistered email
than for a wrong password (D-10), so anyone can test an address and learn whether it has an account.
Password attempts are not limited (D-09), and neither are OTP attempts (D-07). Together, an attacker
can find a real account and then guess against it without interruption.

**Password validation does not match its own message.** `Ab@123` meets every rule the error message
states and is rejected (D-04), while `test@123` breaks the uppercase rule and is accepted (D-05).
Both come from the same root cause and can be fixed in one change.

**Two rules block valid users.** Mobile numbers starting with 97 are refused (D-02) and non-Gmail
addresses are refused (D-06). On a job portal, that is lost signups.

## Files

| File | Contents |
|---|---|
| [signup-test-cases.csv](signup-test-cases.csv) | 28 cases - every field on the registration form |
| [otp-test-cases.csv](otp-test-cases.csv) | 15 cases - verification, expiry, resend, reuse |
| [login-test-cases.csv](login-test-cases.csv) | 21 cases - login validation and session behaviour |
| [defect-log.csv](defect-log.csv) | The 10 defects with severity and reasoning |
| [JOBB_Auth_TestCases.xlsx](JOBB_Auth_TestCases.xlsx) | Full workbook - all sheets, legend and summary |

The CSV files open as tables directly in GitHub. **For the complete detail, including steps, test
data and expected results side by side, open the .xlsx and use the Download raw file button.**

## Method

Cases were designed with equivalence partitioning and boundary value analysis, with negative and
security cases alongside the positive ones. A rule such as a 10-digit phone number was tested at 9,
10 and 11 digits rather than only at a valid value.

There is no requirement document for this project, so expected results were written from the rules
the running build enforces. Failing cases were re-run before being logged. Six session cases are
still marked Not Executed rather than removed.

Project repository: [Aavashjoshi/JOBB](https://github.com/Aavashjoshi/JOBB)
