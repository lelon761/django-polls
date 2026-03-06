# Django Poll Application

This project is a simple poll voting application built using Django.

Users can:

* View poll questions
* Select a choice
* Vote
* View voting results

The Django Admin panel is used to manage questions and choices.



# Prerequisites

**Before running this project, ensure Python and pip are installed.**

* Install Python

&nbsp;	Go to the official Python website:

&nbsp;	https://www.python.org/downloads/

&nbsp;	Download the latest version of Python.

&nbsp;	During installation, make sure to check:

&nbsp;	Add Python to PATH

* After installation, verify Python is installed.

&nbsp;	Open a terminal or command prompt and run:

	**python --version**

&nbsp;	or

	**py --version**

* You should see something like:

&nbsp;	Python 3.x.x

* Verify pip is installed

&nbsp;	Run:

&nbsp;	python -m pip --version

* If pip is missing, install it using:

&nbsp;	python -m ensurepip --upgrade

* &nbsp;Quick test

&nbsp;	Try this command:

&nbsp;		python -m pip install django

If it installs Django, everything is working.



## Setup Instructions

1. Clone the repository

git clone https://github.com/lelon761/django-polls.git

2. Navigate to the project folder

cd django-polls

3. Install required packages

pip install -r requirements.txt

4. Run migrations

python manage.py migrate

5. Start the server

python manage.py runserver

6. Open browser

http://127.0.0.1:8000/polls/

## Admin Login

* URL:
  http://127.0.0.1:8000/admin/
* Username:
  admin
* Password:
  Password1.
