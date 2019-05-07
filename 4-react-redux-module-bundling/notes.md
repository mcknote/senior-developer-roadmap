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

