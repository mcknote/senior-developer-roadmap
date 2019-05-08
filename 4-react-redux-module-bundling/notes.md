# React + Redux + Module Bundling

## Issues to tackle

When websites grow bigger and bigger...

* Maintainability
* Readability
* Bug detection

**SOLUTION**: Framework and library

## State of Front-end Development

Tools of choice:

* Angular
* React
* Vue

Senior developer's perpective: These libraries are just tools, so each one of them is perfect for its own specific use case. *So care less about one specific tool, but more about which tool is good for the job at hand.*

### Thought process on choosing the tool

* Angular
  * Working for a large bank with massive codebase
  * Because Angular is a framework, which means it's an *entire kitchen*
  * Making sure everyone's working in the same kitchen and sticks to the rules
* React
  * Working in a company with strong developer team who also needs to be flexible in adding different tools
  * React is more like an *oven*, good for specific tasks, but most likely we will need to add other tools
* Vue
  * Working for a company that hires a lot of junior developers
  * It offers a simple way of writing code that is easy to get started and understand
  * Vue is like an microwave, super simple and easy to pick up

Reasons of picking React for this course

* It teaches you really good javascript principles that will last you a lifetime beyond just the library
* It has the strongest job demand

## React 

Context

* React was first created by Facebook
* React helps solve the inconsistency issue from jQuery's imperative behoaviour and helps company to scale easier
* It's like a bread machine that takes the ingredients, processes them under the hood, and magically outputs a website
* It's very reliable and very consistent, and it does one thing really well — the view, which makes the DOM change in predictable ways that is easy to scale and easy to manage
* The view is so useful that it is not only used for browsers but also mobile devices to build native apps, VR devices, etc.

### Useful Concepts

* [WHAT IS REACT?](https://lispcast.com/what-is-react/)

#### Components

* Atoms
  * Logo
  * Text
  * Section
* Molecules
  * Combined atoms with similar functionalities
* Organisms
  * Combined molecules for each functionality module
* Templates
  * Combined organisms that tell how the app should work
* Pages
  * Templates with actual data

#### One-way data flow

* Data changes only flow towards one direction, from parent nodes to child nodes
* If a node changes, only its children know about the change

#### Virtual DOM

* Developer's goal: To minimize DOM manipulation
* Previously: Developers are the painters that directly manipulate DOM to create views
* In React: React bots create virtual DOM, a javascript object that describes the current state of our website; developers can just give this object to React, and it will automatically make changes to the DOM and paint the picture in the most optimal way possible

#### Great and extensive ecosystem

* NPM
* Node.js
* Babel
* React router
* Webpack

### What React code looks like

* Classes that extend the react components that we build upon
  * Each class has a mandatory render function to which you can tell what this `clock` should render
  * The syntax is very similar to `HTML`
* Constructor
* Advanced objects

## Create React App

### Preparation

#### Install `create-react-app`

```{bash}
sudo npm install -g create-react-app
```

#### Create an app

```{bash}
create-react-app robofriends
```

#### Start the app

```{bash}
cd robofriends/
npm start
```

#### Files walkthrough

* `package.json`
  * `react-scripts`: includes all the neccesary packages (e.g. Webpack), at the latest version, you would need to build a react app; as the project gets bigger you may use `react-scripts eject` to customize the app
* `package-lock.json`: makes sure the versions of the packages used are correct and the app runs successfully anywhere else
* `.gitignore`: specifies files to ignore while pushing the changes
  * `/node_modules`: we already have `package.json` to install packages needed
* `public/`
  * `index.html`: only has a `<div id='root'>` object in `<body>`
  * `manifest.json`: allows people to download a shortcut to your website
* `src/`
  * `index.js`: has `ReactDOM.render(<App />, document.getElementById('root'))`, which finds the `id='root'` tag in the `index.html` file and renders `App`

### Creation

* [Create React App 2.0: Babel 7, Sass, and More](https://reactjs.org/blog/2018/10/01/create-react-app-v2.html)

#### Update React

1. Change the `react-scripts` (and `react`) version in `package.json` to the latest version
2. Run `npm install` to re-install packages based on `package.json`
3. Run `npm start`

#### Create the first component

* `import`
  * `react` is the core robot that does the rendering
  * `react-dom` is the glue for the Web DOM; by contrast `react-native` can be used for mobile apps
  * `react` supports seperate `css` files for each page, hence the `import './index.css';`
* `ReactDOM`
* `registerServiceWorker()`: for faster performance and offline availability

#### Basic statement

```{js}
import React, { Component } from 'react';

class Hello extends Component {
    render(){
        return <h1>Hello World</h1>
    }
}

export default Hello;
```
