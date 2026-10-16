# Lab 5: Static Code Analysis — Issues Found and Fixes

| Issue | Type | Line(s) Before Fix | Description | Fix Approach |
|---|---|---|---|---|
| Unsafe subprocess call using `shell=True` | Security — High | 61 | Passing a constructed command to a shell can allow command injection. | Replaced the shell command with `shutil.copy2()` to copy the file safely. |
| Mutable default argument | Bug / Code Quality | 12 | Using `history=[]` shares the same list between function calls when no argument is provided. | Changed the default to `None` and initialized a new list inside the function. |
| Overly broad exception handling | Bug / Code Quality | 21–25 | Catching every exception can hide unexpected errors. | Changed `except Exception` to `except KeyError` to handle missing vehicle records specifically. |
| Non-standard function and parameter names | Code Quality | 12, 20, 31, 38, 42, 49, 54, 59 | Names such as `jobCardId`, `vehicleNo`, and `saveRecords` do not follow Python's snake_case convention. | Renamed functions and parameters using snake_case. |
| Missing function docstrings | Code Quality | 42, 49, 54, 59, 64 | Several functions do not explain their purpose. | Added docstrings describing each function. |
| File opened without explicit encoding | Code Quality | 50 | Opening the JSON file without specifying an encoding can cause platform-dependent behavior. | Added `encoding="utf-8"` when opening the file. |
| Missing whitespace and excessive line length | Style | 7, 43, 49, 77 | Formatting did not follow Flake8 and PEP 8 conventions. | Corrected spacing, blank lines, and long lines. |
| Missing final newline | Style | End of file | The file did not end with a newline, causing Pylint and Flake8 warnings. | Added the required final newline. |

## Verification Results

- Pylint: 10.00/10.
- Bandit: No issues identified.
- Flake8: No style issues reported.

The original line numbers refer to the code before fixes. All three tools were rerun on the corrected program.