# Heroku Notes

1. Get Heroku Account: https://signup.heroku.com/login
2. Confirm your email address
3. Install the Heroku Toolbelt - a command-line tool for working with heroku https://toolbelt.heroku.com
4. Use `heroku login` to login with the Heroku Toolbelt.
5. cd into the project directory of you Python Twitter app.
6. Make sure a git repository has been initialized for the project. Do `git status` to check.
7. `heroku create` to create a new app.
8. Goto https://postgres.heroku.com/databases in your browser. Create a PostgreSQL database. Choose "Dev Plan (Free)", and click "Add Database". Wait for the database to finish "preparing..." and become "Available".
9. Click on the database you've created. Take note of the Connection Settings. Enter them into Postico and connect to the DB.
10. Create your DB Schema by running the necessary querys in Postico.
11. We are going to use a Python module called dotenv to manage our database credentials so that they are not version-controlled and made public. Create a .env file and put your DB credentials (from the Heroku PostgreSQL instance). It should look like this:

        DBNAME=YOUR_DBNAME
        DBHOST=YOUR_HOST
        DBPORT=5432
        DBUSER=YOUR_USER
        DBPASSWORD=YOUR_PASSWORD

11B. Create a file called .gitignore (be sure NOT to put anything before the period. Can't STRESS enough that the .gitignore file should be spelled exactly like that: ".gitignore") and put

        .env

in it so that git will not try to commit the .env which contains credentials in it.
12. Install the python-dotenv module: `pip install python-dotenv`
13. In your Python server file (I called mine server.py), add these lines at the top, or at least in the top portion where you do all the imports:

        from dotenv import load_dotenv, find_dotenv
        import os

        load_dotenv(find_dotenv())

14. Still in server.py, replace your db = pg.DB(...) line with:

        db = pg.DB(
          dbname=os.environ.get('DBNAME'),
          host=os.environ.get('DBHOST'),
          port=int(os.environ.get('DBPORT')),
          user=os.environ.get('DBUSER'),
          passwd=os.environ.get('DBPASSWORD')
        )

15. Test your app again locally. It should now be connecting to the remote PostgreSQL database on Heroku instead of your local database.
16. Next, you need to install another python module called gunicorn in order to serve your app more efficiently, and also I couldn't figure out how to get it to work w/o it, so... `pip install gunicorn`
17. Next, to tell Heroku how to start your server, you will create a file named `Procfile`. Put the following content in it:

        web: gunicorn -b 0.0.0.0:$PORT -w 4 server:app

The word **"server"** refers to my server.py, so if you named it something else, you will want to change it to match.



18. Next, Heroku needs to know what Python modules you need for your app so it can install them remotely. To do this, you need a requirements.txt that lists all Python modules you have installed. You can do this with the command: `pip freeze > requirements.txt`
19. 

18.2 Add everything to git - except, of course your .env file. Commit the changes.

19. Deploy your app with `git push heroku master`. The remote repository of "heroku" was already created for you back when you did `heroku create` earlier.


20. Next, you need to configure the database credentials for Heroku as environment variables, line by line

        $ heroku config:set DBNAME=YOUR_DB_NAME
        $ heroku config:set DBHOST=YOUR_DB_HOST
        $ heroku config:set DBPORT=5432
        $ heroku config:set DBUSER=YOUR_USERNAME
        $ heroku config:set DBPASSWORD=YOUR_PASSWORD

Replacing the above values with your own! Or, you can equivalently set all the variables at once using the values you have in the .env file by running this line in your terminal:
###`sed 's/^.*$/heroku config:set &/' .env | bash`
