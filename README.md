# IS 601 - Module 4: Assignment-Interactive Calculator Command-Line
References: https://github.com/kaw393939/module4_is601 for portions of logic and attempts to adhere to the same formatting, with some personal tweaks.

This assignment was to create an interactive calculator for the IS-601 class that creates a calculator that is interactable through a Read-Eval-Print Loop (REPL) interface. Considerations were made towards input validation and error handling.  
Additionally, I added the ability to have a running sum to be more in line with how a traditional handheld calculator functions.  
The instructor repository contained folders such as the .vscode and .coveragerc files; these were ommitted through the .gitignore for my submission, as I felt that these were personal files and wouldn't be commited to a repository under normal circumstances.  
For this module, I continued with my [previous repository for Module 3](https://github.com/adrianchen8662/IS-601-Module-3-Interactive-Calculator), but included the CalculationFactory, along with the necessary unit tests. I had already implemented help and exit, so the only extra special command I added compared to my previous submission is history.  

For testing, code coverage and unit testing was done through the pytest and coverage modules. Github Actions was configured to test merges to main, and to fail if 100% code coverage is not achieved.  
For example, a failed run due to coverage would look like this:  
```
Name                             Stmts   Miss  Cover
----------------------------------------------------
app/calculation/__init__.py          0      0   100%
app/calculation/calculation.py      51      0   100%
app/calculator/__init__.py           2      0   100%
app/calculator/calculator.py        78     11    86%
app/operations/__init__.py           0      0   100%
app/operations/operations.py        15      0   100%
tests/__init__.py                    0      0   100%
tests/conftest.py                   10      0   100%
tests/test_calculation.py          209      1    99%
tests/test_calculator.py            86      0   100%
tests/test_operations.py            25      0   100%
----------------------------------------------------
TOTAL                              476     12    97%
Coverage failure: total of 97 is less than fail-under=100
Error: Process completed with exit code 2.
```


## To Run
```bash
python main.py
```

## To Test
```bash
coverage run -m pytest && coverage report
```
or
```bash
pytest
```

If you are coding on a remote server like I do, a `.coveragrc` file may be needed to allow for the data file to be generated correctly.  
Example .coveragrc file:
```
[run]
data_file = /tmp/.coverage
```

## Notes
Python automatically creates bytecode cache files in the \_\_pycache\_\_ folder. However, these files cause unit tests like coverage and pytest to not update. To remove \_\_pycache\_\_ folders:  
```bash
find . -type d -name "__pycache__" -exec rm -r {} +
```