# Deploy `json-server` to _Heroku_

<img align="right" width="100px" height="auto" src="https://cdn.worldvectorlogo.com/logos/heroku.svg" alt="Heroku">

``


Heroku is a free hosting service for hosting small projects. Easy setup and deploy from the command line via _git_. The cons are that your app will have to sleep a couple of hours every day on the free plan.

###### Pros

* Easy setup
* Free

###### Cons

* App has to sleep a couple of hours every day.
* "Powers down" after 30 mins of inactivity. Starts back up when you visit the site but it takes a few extra seconds. Can maybe be solved with [**Kaffeine**](http://kaffeine.herokuapp.com/)

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

---

### Install Heroku

1. Create an account on <br/>[https://heroku.com](https://heroku.com)
2. Install the Heroku CLI on your computer: <br/>[https://devcenter.heroku.com/articles/heroku-cli](https://devcenter.heroku.com/articles/heroku-cli)

3. Connect the Heroku CLI to your account by writing the following command in your terminal and follow the instructions on the command line:
```bash
heroku login
```


### Create the project

1 . Clone this repo

2 . Change `db.json` to your own content according to the [`json-server example`](https://github.com/typicode/json-server#example) and then `commit` your changes to git.

3 . Then create a remote heroku project, kinda like creating a git repository on GitHub. This will create a project on Heroku with a random name. If you want to name your app you have to supply your own name like `heroku create project-name`:
```bash
heroku create
```

4 . Push your app to __Heroku__ (you will see a wall of code)
```bash
git push heroku master
```

5 . Visit your newly create app by opening it via heroku:
```bash
heroku open
```

6 . For debugging if something went wrong:
```bash
heroku logs --tail
```

---

#### How it works

Heroku will look for a startup-script, this is by default `npm start` so make sure you have that in your `package.json` (assuming your script is called `server.js`):
```json
 "scripts": {
    "start" : "node server.js"
 }
```

You also have to make changes to the port, you can't hardcode a dev-port. But you can reference herokus port. So the code will have the following:
```js
const port = process.env.PORT || 4000;
```
