# React.TS-Vite-Template

## Step One

Open `package.json` and add a `homepage`

<pre>
  "homepage":"https://username.github.io/appName",
</pre>

## Step Two

Install gh pages

<pre>npm install --save gh-pages</pre>

> `yarn` alternative

> <pre>yarn add gh-pages</pre>

Add the following scripts in `package.json`

<pre>
  "scripts": {
+   "predeploy": "npm run build",
+   "deploy": "gh-pages -d build",
    "start": "react-scripts start",
    "build": "react-scripts build",
    ...
  }
</pre>

The `predeploy` script runs automatically before `deploy` is run

## Step Three

> Remove `dist` folder from `.gitignore`

## IMPORTANT NOTICE

> If you are using client side routing and hosting on gh-pages you must use `HashRouter` instead of `BrowserRouter`

Create an `.htaccess` that contains the following

<pre>
Options -MultiViews
    RewriteEngine On
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteRule ^ index.html [QSA,L]
</pre>

## Step Four

Compile the build

<pre>npm run build</pre>

## Step Five

Make sure git knows about your subtree

<pre>git add dist && git commit -m "Initial dist subtree commit"</pre>

## Step Six

Use subtree push to send it to gh-pages branch on GitHub

<pre>git subtree push --prefix dist origin gh-pages</pre>
