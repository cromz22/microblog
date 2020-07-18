# Twitter-like app

## Reference
[The Flask Mega-Tutorial](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world)

## Usage
Make sure venv is activated:
```
. venv/bin/activate
```

### Run
#### Run
```
flask run
```
You will see the app running on `localhost:5000`.
#### Run interactively
```
flask shell
```
A python interpreter with the app-dependent variables will start.

### Test
#### Test registration, posting, following/unfollowing
```
python tests.py
```
#### Mail test
1. Open new shell (say shell 1) and run a mail server:
```
python -m smtpd -n -c DebuggingServer localhost:8025
```
2. In the project directory (say shell 2), set two environment variables:
```
source mail_test.sh
```
3. If you send an email from shell 2, you will get it on shell 1.

## Data Flow
1. When the server is started, an app instance is created (`__init__.py`). It reads its configurations from `config.py`, sets up the database, and do some other initialization tasks.
1. A user goes to the page and sends a HTTP request.
1. Corresponding function in `app/routes.py` is called. It may call another functions, e.g. form functions in `app/forms.py`. It calls `render_template` function at the end.
1. `render_template` returns the corresponding template from `app/templates/`. The templates may involve arguments in the `render_template` function.
1. Now the user can see the page. If she/he sends another request, go back to 2.
