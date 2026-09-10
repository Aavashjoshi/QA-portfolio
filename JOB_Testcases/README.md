# Career Connect - Job Module Testing

Manual testing of the job module of Career Connect, a MERN job portal. Covers posting a job as a
recruiter, and searching, filtering and viewing jobs as a jobseeker. The app was run locally and
every case was run by hand in the browser.

**55 test cases | 54 run | 6 defects | 90.7% pass**

| | Post Job | Search | Filter | Detail | Total |
|---|---|---|---|---|---|
| Cases | 22 | 12 | 10 | 11 | **55** |
| Pass | 21 | 9 | 9 | 10 | **49** |
| Fail | 3 | 3 | 0 | 0 | **6** |
| Not run | 0 | 0 | 0 | 1 | **1** |

## Defects

| ID | Test case | Summary | Severity |
|---|---|---|---|
| JD-01 | TC_JOB_007 | Salary of zero is allowed, but a minus salary is blocked | Medium |
| JD-02 | TC_SRC_004 | An empty search shows no jobs at all | Medium |
| JD-03 | TC_SRC_002 | No message when a search or filter finds nothing | Low |
| JD-04 | TC_SRC_006 | Search does not look at the job description | Low |
| JD-05 | TC_JOB_002 | The message does not say which field is missing | Low |
| JD-06 | TC_JOB_005 | Messages do not always start with a capital letter | Low |

## Main points

A salary of -5000 is blocked, but a salary of 0 is saved and the job goes live. The same form blocks
0 correctly in the No of Position field, so the two fields do not follow the same rule.

Pressing search with an empty box shows nothing at all. It should show all jobs, or ask the user to
type something.

Four defects were expected after reading the source code: a second search not refreshing, two
filters returning nothing, the job list ignoring its sort order, and a bad job ID leaving the page
loading. All four were tested and none of them are in this build.

## Files

| File | Contents |
|---|---|
| [post-job-test-cases.csv](post-job-test-cases.csv) | 22 cases - the Post Job form |
| [job-search-test-cases.csv](job-search-test-cases.csv) | 12 cases - the search box |
| [job-filter-test-cases.csv](job-filter-test-cases.csv) | 10 cases - location and industry filters |
| [job-detail-test-cases.csv](job-detail-test-cases.csv) | 11 cases - job detail and recruiter job list |
| [defect-log.csv](defect-log.csv) | The 6 defects |
| [JOBB_Job_TestCases.xlsx](JOBB_Job_TestCases.xlsx) | Full workbook |

The CSV files open as tables here in GitHub. **The full workbook is in this folder too. For the
complete detail - steps, test data, expected and actual results side by side - open the .xlsx and
use the Download raw file button.**

## Method

Cases were designed with equivalence partitioning and boundary value analysis. Number fields like
Salary and No of Position were tested at zero, below zero and with letters, not just with a correct
value.

There is no requirement document for this project, so expected results were written from the rules
the running app follows. TC_JDT_006 is marked Not run because the result recorded did not answer
what the case was written to check.

Project repository: [Aavashjoshi/JOBB](https://github.com/Aavashjoshi/JOBB)
