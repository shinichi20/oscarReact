# Guide on how to create and set up your Django project with webpack, npm and ReactJS :)
Hopefully this will answer *"How do I setup or start a Django project?"*
I was trying to set up my own website, and there was a lot to read, learn and digest!
Therefore, I put this together which is a collection of all the guides/blog posts/articles that I found the most useful.
At the end of this, you will have your barebones Django app configured and ready to start building :)

**NOTE:** This guide was built using Django 1.9.5, NodeJS 4+ with NPM 3+

## 1. Setting up your dev environment

If working on Mac OSX, follow this [guide](https://gist.github.com/genomics-geek/e3b6823cd03272f0ba8268cf9063c335).

### Requirements
+ PostgreSQL
+ virtualenv
+ virtualenvwrapper
+ git
+ NodeJS 4+ with NPM 3+

## 2. Create a Virtual Environment

It’s common practice to use a virtual environment for your Python projects in order to create self-contained development environments. The goal of virtualenv is to prevent different versions of libraries/packages from messing with each other. It’s like an isolated, soundproof room within your home where you can scream as loud as you want, about anything you want, and nobody else outside that room can hear it.

Use virtualenvwrapper to create a virtual environment for your project:
```
mkvirtualenv -p /usr/local/bin/python3 [project-name]
```

After running this command you should see (project-name) before your prompt, indicating that you’re running within the ```project-name``` virtualenv.

You should see something like this:
```
(project-name) MacBook-Air:~ michaelgonzalez$
```

## 3. Install Python packages

I start off every project with the same 7 Python packages:
```
pip install django-webpack-loader
pip install dj-database-url
pip install django
pip install gunicorn
pip install psycopg2
pip install python-decouple
pip install requests
pip install whitenoise
```

## 4. Create a directory for your Django project

This one is easy:
```
mkdir [project-name]
cd [project-name]
```

## 5. Setup Django project

Now lets automagically generate some code that establishes a Django project. Run the following command:
```
django-admin startproject [project-name] .
```

This should have created the following folder structure:
```
[project-name]/
    manage.py
    [project-name]/
        __init__.py
        settings.py
        urls.py
        wsgi.py
```

## 6. Create README.md file

This file will obviously be very simple to start, but it doesn't hurt to start describing your project :). You can fill in all the details as you develop! Make sure to visit this [Markdown cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet), which will allow you to create well designed and organized README files.

## 7. Create .gitignore file

This file will specify intentionally untracked files that Git should ignore. For more info, look [here](https://git-scm.com/docs/gitignore).

The contents of ```.gitignore```:
```
venv
*.pyc
staticfiles
.env
env
node_modules
[project-name]/static/build
db.sqlite3
.DS_Store
__pycache__
```

## 8. Use git and GitHub for version control

I personally choose to use git for my software version control. I also use GitHub, which is a web-based Git repository hosting service. These tools help with deployment, working on teams, etc. This makes your life so much easier, trust me!

First things first, make sure to create a new repo at GitHub.com and __DO NOT__ initialize with a README.md.

After you have created the repo, run these commands:
```
git init
git add .
git commit -m "first commit"
git remote add origin https://github.com/user-name/[project-name].git
git push -u origin master