# Order Up!

## Using this Repo
This repo is to be used as a supplemental resource for the Flask-SQLAlchemy 
project Order Up! In this README, I'll document anything I find that's a bit
out of order, lacking in clarity or seemingly missing from the project.

## Getting started: dependencies and database
```
create user order_up with password '9uCxydbt';
create database order_up_dev with owner order_up;
```
Is unnecessary, can instead simply create a new db, I went with 
```
touch order_up.db
```

## Adding SQLAlchemy
The article [Using SQLAlchemy With Flask][Using SQLAlchemy With Flask] is found
on Week 36's Monday content.

Sample `config.py`
```py
import os


class Configuration:
    SECRET_KEY = os.environ.get('SECRET_KEY')
    SQLALCHEMY_DATABASE_URI=os.environ.get('DATABASE_URL')
    SQLALCHEMY_TRACK_MODIFICATIONS = False
```
Sample `.env`
```
FLASK_DEBUG=True
SECRET_KEY=qp02348jrqj43rpqj34pqjr
DATABASE_URL=sqlite:///dev.db
```



<!-- Links for feb cohort -->
[Using SQLAlchemy With Flask]: https://open.appacademy.io/learn/js-py---pt-feb-2022-online/week-36---sqlalchemy-and-alembic/using-sqlalchemy-with-flask