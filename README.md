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

## The Employee Mapping Class
Articles can again be found on Monday

[SQLAlchemy Mappings][SQLAlchemy Mappings]

[Using SQLAlchemy With Flask][Using SQLAlchemy With Flask]

We'll need to make sure we've got the imports specified in the directions,
then we can continue to create the model as described.
Since we haven't seen it yet, the basic format for a Model in SQLAlchemy is:
```py
class TableName(db.model, <optional additional classes>):
    __tablename__= "name_of_your_table_goes_here"

    # column_name = db.Column(db.dataType(constraints), properties=Value)
    # examples below
    id = db.Column(db.Integer, primary_key=True) 
    # create PK id
    name = db.Column(db.String(100), nullable=False, unique=True) 
    # create name, string length 100, not nullable, must be unique
```
That format should guide you through creating a model, but, if you're struck
you can refer to [models.py][models.py]

## The LoginForm
Not too much new here, but I thought it might be useful to talk about 
`extends`. This keyword in Jinja is basically tells a template that it should
`extend` the code found in the specified template. In this case, our
`login.html` will get included with our `base.html`. Notice inside of
`base.html` the body has `{% block content %}{% endblock %}`, and in our
`login.html` we've got both as well, however notice that they are instead
wrapping the entirety of the template that we wish to render. Jinja will match up
our blocks and fill in our code where necessary.

## Making the login view
The instructions aren't particularly clear here, but most of the unknown values
in the given code can be gotten from `flask_login`.

## Log out form
Don't overthink the part about making the logout form go away. If
current_user.is_anonymous holds the value of true, how can we take the opposite
of that?

## Menu model and data
[SQLAlchemy Mappings][SQLAlchemy Mappings] may be useful when trying to figure
out how to make your relationships on your model. `back_populates` is such a
handy attribute to have access to!




<!-- Repo links -->
[models.py]: ./app/models.py

<!-- Links for feb cohort -->
[Using SQLAlchemy With Flask]: https://open.appacademy.io/learn/js-py---pt-apr-2022-online/week-36---sqlalchemy-and-alembic/using-sqlalchemy-with-flask
[SQLAlchemy Mappings]: https://open.appacademy.io/learn/js-py---pt-apr-2022-online/week-36---sqlalchemy-and-alembic/sqlalchemy-mappings
[Using SQLAlchemy With Flask]: https://open.appacademy.io/learn/js-py---pt-apr-2022-online/week-36---sqlalchemy-and-alembic/using-sqlalchemy-with-flask
