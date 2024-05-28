# Django project deployment(Use for all future Django projects)
Download Heroku first through the installer(https://cli-assets.heroku.com/channels/stable/heroku-x64.exe) for the heroku Command Line interface
- create django project through pycharm and Create Procfile and add (web: gunicorn pages_project.wsgi --log-file -) to the file.
### manage.py startapp posts 
- (this will automatically add 'posts.apps.PostConfig' in the settings.py file in the INSTALLED_APPS variable.
- Work on project and once finished follow below steps..
### pip install pipenv
### pipenv install django
### pipenv shell
### pipenv install gunicorn
- To generate appropriate Pipfile.lock. Generally pycharm does this automatically enter the code below:
### pipenv lock 
- In the settings file under the ALLOWED_HOSTS, key in the your respective domain, if you dont care about the domain use ALLOWED_HOSTS = [*]
  - NB - The ALLOWED_HOSTS setting represents which host/domain names our
Django site can serve. This is a security measure to prevent HTTP Host
header attacks, which are possible even under many seemingly-safe web
server configurations. However we’ve used the wildcard Asterisk * which
means all domains are acceptable to keep things simple. In a production-level
Django site you would explicitly list which domains were allowed.
-  Commit and push project to github
## Next process
- create a new app on Heroku and push our code to it
  ### heroku create
     - Creating app... done, ⬢ fathomless-hamlet-26076
https://fathomless-hamlet-26076.herokuapp.com/ |
https://git.heroku.com/fathomless-hamlet-26076.git
- add a git remote “hook” for Heroku
  ### heroku git:remote -a fathomless-hamlet-26076
     - You should replace fathomless-hamlet-26076 with the app name Heroku provides.
- configure the app to ignore static files
  - If you only need to do one set of Heroku configurations, tell Heroku to ignore static files like CSS and JavaScript which Django by default tries to optimize for us
  ### heroku config:set DISABLE_COLLECTSTATIC=1
- Now we can push our code to Heroku. Because we set our “hook” previously, it will go to Heroku.
  ### git push heroku master
- Finally we need to make our Heroku app live. As websites grow in traffic they need additional Heroku services but for our basic example we can use the lowest level, web=1, which also happens to be free!
  ### heroku ps:scale web=1
- We’re done! The last step is to confirm our app is live and online. If you use
the command heroku open your web browser will open a new tab with the
URL of your app:
  ### heroku open

#### The project uses basic templates, class based views, explored URLConfigurations, basic tests and Heroku.


