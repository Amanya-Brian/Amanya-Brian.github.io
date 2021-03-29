---
layout: post
title:  "A Quick Guide To Setting Up ElectronJS"
description: "How to set up electronJS"
date:   2021-03-24 12:03:42 +0300
categories: jekyll update
---
# This will help you get started and set up ElectronJS
## What is ElectronJS?
Electron JS is a JavaScript framework that is used to create desktop applications using HTML, CSS and JavaScript. The beauty with ElectronJS is that it supports multiple platforms, that is, your desktop applications can be packaged to run on Windows, MacOS and Linux OS. It runs on the Chromium engine.
Another thing is that it does not require special learning or any extra skill to get started.

## What do I need to get started with ElectronJS?
You need to have node.JS installed on your machine before you can get started with Electron. You can easilt check this in your terminal by running these commands;
{% highlight ruby %}
node -v
npm -v
{% endhighlight %}
These command should return the versions of node.JS and npm that are installed on your machine. These should preferrably be the latest versions.

## Setting up your first ElectronJS application, Hello World!
Start by creating a folder and install Electron in it:
{% highlight ruby %}
mkdir electron-app
cd electron-app
npm init -y
npm i --save-dev electron
{% endhighlight %}
This will set up a basic ElectronJS application with a *node_modules* directory, a *package.json* file and a *package_lock.json* file. However, the minimum basic structure looks like this:
{% highlight ruby %}
my-electron-app/
├── package.json
├── main.js
├── preload.js
└── index.html
{% endhighlight %}
ElectronJS has two essential processes: the main process and the renderer process. The main process is the entry point of the application and launches the renderer process. The renderer process renders the app(HTML, JS and CSS). 
We shall create the missing files as we move along. The communication between the two processes is done using the *InterProcess Communication(IPC)*.
### Creating the main script file
The main script file(usually named main.js) is the entry point of the application and it runs the Main process, as mentioned earlier. It controls the lifecycle of the application, displays the graphical user interface and its elements, performs native operating system interactions, and creates Renderer processes within web pages. An Electron application can have only one Main process.
Take a look at the minimal main.js file:

{% highlight ruby %}
const { app, BrowserWindow } = require('electron')
const path = require('path')

function createWindow () {
  const win = new BrowserWindow({
    width: 800,
    height: 600,
    webPreferences: {
      preload: path.join(__dirname, 'preload.js')
    }
  })

  win.loadFile('index.html')
}

app.whenReady().then(() => {
  createWindow()

  app.on('activate', () => {
    if (BrowserWindow.getAllWindows().length === 0) {
      createWindow()
    }
  })
})

app.on('window-all-closed', () => {
  if (process.platform !== 'darwin') {
    app.quit()
  }
})

{% endhighlight %}

#### Brief explanation:
* We start by importing the <mark>app</mark> and <mark>BrowserWindow</mark> modules of the <mark>electron</mark> package to be able to manage lifecycle events, and also create and manage browser windows.
* We import the <mark>path</mark> package which provides utility functions for file paths.
* The <mark>createWindow</mark> function is defined to create a new browser window with a preload script that loads the html files available.
* The <mark>app.whenRerady()</mark> function calls the <mark>createWindow</mark> function when the app is initialised thereby creating a new browser window.
* Add a new listener that creates a new browser window only if when the application has no visible windows after being activated. For example, after launching the application for the first time, or re-launching the already running application.
* Add a new listener that tries to quit the application when it no longer has any open windows.

### Creating the HTML page
This is the page that is displayed once the app is initialised. This initiates the Renderer process mentioned earlier. It is possible to create multiple windows, each using its own Renderer. Optionally, you can allow additional Node.js APIs by exposing them from your preload script.
Create an <mark>index.html</mark> file with the following contents:
{% highlight ruby %}
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Hello World!</title>
    <meta http-equiv="Content-Security-Policy" content="script-src 'self' 'unsafe-inline';" />
</head>
<body style="background: white;">
    <h1>Hello World!</h1>
    <p>
        We are using Node.js <span id="node-version"></span>,
        Chromium <span id="chrome-version"></span>,
        and Electron <span id="electron-version"></span>.
    </p>
</body>
</html>
{% endhighlight %}

### The preload script
This acts as the bridge between Node.JS and your web page. It allows you to expose specific APIs and behaviors to your web page rather than insecurely exposing the entire Node.js API. Here, we will use the preload script to read version information from the <mark>process</mark> object and update the web page(HTML) with that info.
Create a <mark>preload.js</mark> file with the following contents:

{% highlight ruby %}
window.addEventListener('DOMContentLoaded', () => {
  const replaceText = (selector, text) => {
    const element = document.getElementById(selector)
    if (element) element.innerText = text
  }

  for (const type of ['chrome', 'node', 'electron']) {
    replaceText(`${type}-version`, process.versions[type])
  }
})

{% endhighlight %}

#### Brief explanation:
* We start by adding an event listener when the webpage has loaded.
* Then you define a utility function that replaces the place holders in the *HTML file* 
* Loop through the contents whose versions you are to display
* Call the *replaceText()* function to look up the version placeholders in *index.html* and set their text value to the values from <mark>process.versions</mark>.

### Modifying the package.json file
Like any other Node.JS application, the *package.json* is the main entry point for this Electron application. We need to modify it to suit our current application needs.

{% highlight ruby %}
{
  "name": "electron-app",
  "version": "1.0.0",
  "description": "",
  "main": "main.js",
  "scripts": {
    "start": "electron .",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "your_name",
  "license": "ISC",
  "devDependencies": {
    "electron": "^12.0.2"
  }
}

{% endhighlight %}

#### Brief explanation:
* Change the *main* key to have a value of *main.js* since it is the main script of the application.
* In the *scripts* array, add the *start* key with a value of *electron* so that the script runs with Electron.
* The *author* and *description are very important during packaging and if not defined, an error will occur.

### Running the application
We are done! You can run the new Electron app using:
{% highlight ruby %}
npm start
{% endhighlight %}