# Loan Management

This is an Online Banking Concept with Loan Management created using Django Web Framework.


## Features

* Create Bank Account.
* Deposit & Withdraw Money
* Bank Account Type Support (e.g. Current Account, Savings Account)
* Interest calculation depending on the Bank Account type
* Transaction report with a date range filter 
* See balance after every transaction in the Transaction Report
* Calculate Monthly Interest Using Celery Scheduled tasks
* POST API View to register a User’s (availing the loan) details
* POST API View to apply & initiate a User Loan
* EMIs calculation 
● Interest is incurred starting from next day of disbursal
● All due amounts should be paid back within tenure. All EMI amounts should be the same
except the last which can be less than the other EMIs. Note
● last EMI amount settles all pending dues.
● EMIs consists of (formula to be deduced by you)
● Part of Principal amount due
● Interest on that principal amount for that month
● EMI amount must be at-most 60% of the monthly income of the User
● Interest rate should be >=14%
● Total interest earned should be >10000
● All EMIs will be due on 1st of every month starting from the following month of
disbursement

* POST API to register payment made
* GET API to get statement and future dues
* Response fields
  ● Error: None if no error. Error String in case of failure
● Past_transactions: Empty list for no past transactions. For valid transactions, each object
contains:
- Date
- Principal
- Interest
- Amount_paid
- Upcoming_transactions: List containing objects of EMI dates and amount. Each
object contains:
- Date: EMI date
- Amount_due: Amount due on that date.
* More efficient and accurate interest calculation and balance update
* Ability to add Minimum and Maximum Transaction amount restriction
* Modern UI with Tailwind CSS


## Prerequisites

Be sure you have the following installed on your development machine:

+ Python >= 3.7
+ Redis Server
+ Git
+ pip
+ Virtualenv (virtualenvwrapper is recommended)

## Requirements

+ celery==4.4.7
+ Django==3.2
+ django-celery-beat==2.0.0
+ python-dateutil==2.8.1
+ redis==3.5.3

## Install Redis Server

[Redis Quick Start](https://redis.io/topics/quickstart)

Run Redis server
```bash
redis-server
```

## Project Installation

To setup a local development environment:

Create a virtual environment in which to install Python pip packages. With [virtualenv](https://pypi.python.org/pypi/virtualenv),
```bash
virtualenv venv            # create a virtualenv
source venv/bin/activate   # activate the Python virtualenv 
```

or with [virtualenvwrapper](http://virtualenvwrapper.readthedocs.org/en/latest/),
```bash
mkvirtualenv -p python3 {{project_name}}   # create and activate environment
workon {{project_name}}   # reactivate existing environment
```

Clone GitHub Project,
```bash
git@github.com:saadmk11/banking-system.git

cd banking-system
```

Install development dependencies,
```bash
pip install -r requirements.txt
```

Migrate Database,
```bash
python manage.py migrate
```

Run the web application locally,
```bash
python manage.py runserver # 127.0.0.1:8000
```

Create Superuser,
```bash
python manage.py createsuperuser
```

Run Celery
(Different Terminal Window with Virtual Environment Activated)
```bash
celery -A banking_system worker -l info

celery -A banking_system beat -l info
```
