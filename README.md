
# SPAllinsonJS - Beginner App

v1.4.0



## Description

A basic app outlining SPAllinsonJS fundamentals.

Topics include: Routing, Components, History, Deeplinking, Bookmarking



## See it in Action

[www.spallinsonjs.com/example-apps/beginner](http://spallinsonjs.com/example-apps/beginner)



## Getting Started

You'll need a web server to run the app.

Here are a couple of options:

- [Node.js](https://nodejs.org/en/) (Mac/Windows/Linux)
- [MAMP](https://www.mamp.info/en/downloads/) (Mac)
- [WAMP](http://ampps.com/wamp) (Windows)



## App Architecture

The app is made up of the following files:
- `index.html`
- `app/common.css`
- `app/settings.js`
- `components/main-template/*`
- `components/page-one/*`
- `components/page-two/*`
- `components/page-three/*`
- `spallinsonjs/*`

#### index.html

The `index.html` file is very simple.

It sets some meta tags and imports:
- SPAllinsonJS
- the app's `settings.js` file
- the `common.css` styles file
- the components' `.css` files

Notice that the `<body>` is left blank! SPAllinsonJS will stitch everything together using information from `settings.js`. Also notice that the components' `.js` files are not imported. They are also read from `settings.js`.

#### app/common.css

Common css styles shared across the application.

#### app/settings.js

The `settings.js` file contains `_A_.Settings`, which helps control the app. There are quite a lot of keys on the `_A_.Settings` object. We'll look at a few in this first example app, and address the rest later.

###### _A_.Settings.initialRoute

Notice that the `initialRoute` is `main/pageone`. This indicates to SPAllinsonJS that when the app launches, you want it to first route to `main`, then to `pageone`.

`main` and `pageone` are called routes.

###### _A_.Settings.routes

A "route" is an array of "component to div" mappings (with optional fade out / fade in transition).

`pageone` says to route the `PageOne` component into the div with id `mainContainer`. `pagetwo` says to route the `PageTwo` component into ... etc.

`main` though says to route the `MainTemplate` component into `app`.

`app` (or `''`) can be used to route a component into the application's top level, full-screen container!

###### _A_.Settings.components

This is where you "register" all of the components the app will use.

A SPAllinsonJS component follows the MVC design pattern. MVC stands for Model View Controller, which is a way to separate logic, allowing for maximum reuse, and code that is easier to understand, and test!

A component requires a `view`, but does not require a `controller`, `pageTitle`, or `preload` value. `view` can take a string or a function that returns a string.

This first app is quite simple and only has 4 components: `MainTemplate`, `PageOne`, `PageTwo`, and `PageThree`.

If you look into the `components` folder, you'll see the files for these components.

Look into the `main-template` folder ...
- The View is the `main-template.html` file
- The Controller is the `main-template.js` file
- The Model is a JS object SPAllinsonJS injects into the instance of the controller

The View is made up of a header and a content container. Buttons have been added to control the navigation. These buttons call methods on the controller. `_C_.prevPressed()` tells SPAllinsonJS that you want to call the `prevPressed` method on the component's controller. If you look at the Controller, you'll find said method.

`_C_` allows you access to public methods on a component's controller!

To make a method or variable public, add it onto `this` of the controller. Private methods and variables can also be achieved simply by assigning them to locally scoped variables.

The rest of the controller's logic handles routing the 3 pages into the `mainContainer` div (based on the `currentPage`). The controller determines the desired page and then routes.

`_A_.Go()` is how to perform routing in SPAllinsonJS.

Notice the use of `_A_.Go('../pagethree')`. The double dot (`../`) can be used (much like a file path) to replace the last route. A single dot (`./`) can be used to append a route to the current routing.

`_A_.Router.currentRoute` was used to determine the initial value for `currentPage` (required for handling reloading/deeplinking).

###### _A_.Settings.fallbackRoute

If ever SPAllinsonJS errors out trying to perform a routing, then it will route the user to the `fallbackRoute`. This can happen if the user enters a bogus url, if there are software bugs (e.g. route does not exist, spelling mistakes), etc..

#### components/*

This folder holds all of the components' files.

#### spallinsonjs/*

This is the v1.4.0 release of SPAllinsonJS. Nothing to see here.



## History / Bookmarking / Deeplinking

SPAllinsonJS's router handles browser history, and allows for bookmarking of pages as well as deeplinking to specific pages (e.g. from an email link)!

Try it out by navigating to page three, then:
- go back in history
- reload the page
- bookmark the page
- copy the url and enter it into a different browser window



## SPAllinsonJS Documentation

#### Example Apps

- Beginner App
- [Intermediate App](https://github.com/SPAllinsonJS/spallinsonjs-example-intermediate)
- [Advanced App](https://github.com/SPAllinsonJS/spallinsonjs-example-advanced)

#### Docs

All documentation can be found on the official site: [www.spallinsonjs.com](http://www.spallinsonjs.com)



## Copyright

All content &copy; [Chris J. Allinson](http://www.allinson.ca) 1996 - Present. All rights reserved.
