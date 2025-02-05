# Unit Testing with Pytest

## Overview

Pytest is one of the primary unit testing frameworks for Python. We're going to look at a short example, then practice generating a few additional test cases.

## Code

Put this code in a file named `calculator.py`:
```
class Calculator:
    def add(self, a, b):
        return a + b
    
    def divide(self, a, b):
        if b == 0:
            raise ValueError("Cannot divide by zero")
        return a / b
```

Put the following code in a file named `test_calculator.py`:
```
import pytest
from calculator import Calculator

class TestCalculator:
    @pytest.fixture
    def calculator(self):
        return Calculator()
    
    def test_add(self, calculator):
        assert calculator.add(2, 3) == 5
        assert calculator.add(-1, 1) == 0
        assert calculator.add(0, 0) == 0
    
    def test_divide(self, calculator):
        assert calculator.divide(6, 2) == 3
        assert calculator.divide(5, 2) == 2.5
        
    def test_divide_by_zero(self, calculator):
        with pytest.raises(ValueError) as exc_info:
            calculator.divide(1, 0)
        assert str(exc_info.value) == "Cannot divide by zero"
    
    @pytest.mark.parametrize("a,b,expected", [
        (3, 4, 7),
        (-2, 3, 1),
        (0, 0, 0),
    ])
    def test_add_parameterized(self, calculator, a, b, expected):
        assert calculator.add(a, b) == expected
```

## Run

Start by intalling `pytest`:
```
pip install pytest
```

You can then run all files starting with `test_` in the current directory using
```
pytest -v
```
(the `-v` flag is for verbose mode to produce additional output on each test).

If that doesn't work, try
```
python -m pytest -v
```
The `-m` flag allows you to run a specific module as if it was invoked from the command line.

## Break

Edit the `add` method in `calculator.py` to return an incorrect result, then run the tests again. Verify that the test fails.


## Questions

Once you can verify the tests work, answer the following questions. Feel free to use your chat interface to help:

- What does `assert` do?

- What does `@pytest.fixture` do?

- How does the `test_add` method work? How does it get the input `calculator` parameter that it uses?

- What does `@pytest.mark.parametrize` do?

- How does `test_divide_by_zero` work? What is the `assert` statement testing?


## Change

Add a new method called `mul` to the calculator that implements multiplication. Then use your editor to generate new unit tests in `test_calculator` to exercise the new method. Try creating one that follows the same format as `test_add`, then one that uses the `parameterize` technique.

Write another method called `abs` that takes a number and returns its absolute value. Use an `if`-`else` statement to implement.

- How many test cases should you create for `abs`?
- Generate test code and verify that it works.
