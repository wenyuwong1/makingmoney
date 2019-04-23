# Calculating Hourly Wage with Military Time-In/Time-Out

Write a Python program called `makingmoney.py` that takes exactly two optional `-s` start time and `-e` end time arguments which should be two military time stamp values representing start and end time of a work shift. Set both arguments to `required=True`. The program should also accept a `-w|--wage` option (integer) which is the wage amount that the person will be earning (default:8).

If both the start and end time is given, calculate the hour wage that the person will be earning. Print a statement indicating their start and end time, a statement of how long they worked, and the total amount of money earned. 

If either start or end time is not given in military format, print an error message.

# Expected Behavior

````
$ ./makingmoney.py
usage: makingmoney.py [-h] -s HH:MM -e HH:MM [-w int]
makingmoney.py: error: the following arguments are required: -s/--start, -e/--end

$ ./makingmoney.py -h
usage: makingmoney.py [-h] -s HH:MM -e HH:MM [-w int]

Making Money script

optional arguments:
  -h, --help            show this help message and exit
  -s HH:MM, --start HH:MM
                        Military Time-In (default: None)
  -e HH:MM, --end HH:MM
                        Military Time-Out (default: None)
  -w int, --wage int    The wage a person earns (default: 8)

$ ./money.py -s 14:00 -e 9:00
usage: money.py [-h] -s HH:MM -e HH:MM [-w int]
money.py: error: argument -e/--end: invalid fromisoformat value: '9:00'

$ ./makingmoney.py -s 09:00 -e 13:00
You started at 09:00:00 and ended at 13:00:00
You worked for 4:00:00 hours
You earned $32.00

$./makingmoney.py -s 09:00 -e 13:00 -w 14.25
You started at 09:00:00 and ended at 13:00:00
You worked for 4:00:00 hours
You earned $57.00

````

# Test Suite

A passing test looks like this:

````
$ make test
pytest -v test.py
========================================== test session starts ==========================================
platform linux -- Python 3.7.1, pytest-4.0.2, py-1.7.0, pluggy-0.8.0 -- /rsgrps/bh_class/conda/bin/python
cachedir: .pytest_cache
rootdir: /rsgrps/bh_class/wwong3/biosys-analytics/assignments/14-open, inifile:
plugins: remotedata-0.3.1, openfiles-0.3.1, doctestplus-0.2.0, arraydiff-0.3
collected 4 items                                                                                       

test.py::test_usage PASSED                                                                        [ 25%]
test.py::test_bad_input PASSED                                                                    [ 50%]
test.py::test_ok1 PASSED                                                                          [ 75%]
test.py::test_ok2 PASSED                                                                          [100%]


=========================== 7 passed in 2.94 seconds ===========================
````
