# Coffee Shop Backend

## Getting Started

### Python 3.7
You need to have Python version 3.7 installed. Follow [this link](https://docs.python.org/3.7/using/unix.html#getting-and-installing-the-latest-version-of-python) to install Python 3.7.

### Virtual Environment
It is recommended to run the project on virtual enviroment, so the dependencies don't get mixed up with the dependencies you have installed on your system.

Enter this commands in terminal to set it:
```
py -3.7 -m venv venv
venv\Scripts\activate 
```
or if this doesn't work try:
```
python3.7 -m venv venv
source venv\Scripts\activate 
```

### Installing Dependencies
The dependencies needed for this projects are in `/backend/src/requirements.txt`.

To instal them, make sure you have the virtual enviroment running, then cd into `backend` and run:
```
pip install -r requirements.txt
```
or if it doesn't work:
```
pip3 install -r requirements.txt
```

This will install all of the required packages we selected within the `requirements.txt` file.

##### Key Dependencies

- [Flask](http://flask.pocoo.org/) is a lightweight backend microservices framework. Flask is required to handle requests and responses.

- [SQLAlchemy](https://www.sqlalchemy.org/) and [Flask-SQLAlchemy](https://flask-sqlalchemy.palletsprojects.com/en/2.x/) are libraries to handle the lightweight sqlite database. Since we want you to focus on auth, we handle the heavy lift for you in `./src/database/models.py`. We recommend skimming this code first so you know how to interface with the Drink model.

- [jose](https://python-jose.readthedocs.io/en/latest/) JavaScript Object Signing and Encryption for JWTs. Useful for encoding, decoding, and verifying JWTS.

## Running the server

From within the `./src` directory first ensure you are working using your created virtual environment.

Run:

```
export FLASK_APP=api.py;
```
or if it doesn't work:
```
set FLASK_APP=api.py
```
or
```
$env:FLASK_APP = "api.py"
```
...

To run the server, execute:

```
flask run --reload
```
or if it doesn't work:
```
python -m flask run --reload
```

The `--reload` flag will detect file changes and restart the server automatically.
