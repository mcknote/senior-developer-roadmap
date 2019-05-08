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

```sh
sudo npm install -g create-react-app
```

#### Create an app

```sh
create-react-app robofriends
```

#### Start the app

```sh
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

In the `App/Hello.js` file...

```jsx
import React, { Component } from 'react';
import './Hello.css';

class Hello extends Component {
    render(){
        return (
            <div>
                <h1>Hello World</h1>
                <p>Welcome to React</p>
            </div>
        );
    }
}

export default Hello;
```

In the `src/Hello.css` file...

```css
h1 {
    background: red;
}
```

#### Use `tachyons` to boost development

Install `tachyons`

```sh
npm install tachyons
```

Import `tachyons` in `src/index.js`

```jsx
import 'tachyons'
```

And then start using `tachyons` in `src/Hello.js`

```jsx
import React, { Component } from 'react';
import './Hello.css';

class Hello extends Component {
    render(){
        return (
            <div className='f1 tc'>
                <h1>Hello World</h1>
                <p>Welcome to React</p>
            </div>
        );
    }
}

export default Hello;
```

**Why we use `className` instead of `class`** is because this is actually follows the `jsx` syntax which limits our changes to the virtual DOM and allows `react` to perform minimum DOM manipulations.

Also, since in this `js` file the `class` keyword is already reserved, it may cause confusion if we use `class` again in the `html` portion for other purposes. Here `className` helps separate the ohter usage.

#### Use of Seggregation of Concerns

In `react` each component consists of both content, the stylesheet and the action. Although this seems to violate SoC, in fact because component is regarded as basic functionality unit within `react`, this helps developers to focus on the compnent itself to make any changes.

In the downstreams different atoms are still separate, so component actually acts as a nice interim level that already intergrates the trinity.

#### Adding `props`

If we add the `props` (properties) in the `src/index.js` file as follows:

```jsx
...
ReactDoM.render(<Hello greeting={'Hello' + 'React Ninja'}>, document.getElementById('root'))
...
```

We may use this `prop` in our `src/Hello.js` file:

```jsx
...
<h1>Hello world</h1>
<p>{this.props.greeting}</p>
...
```

This basically means we want to use the `greeting` property from this `Hello.js` file, which is defined from the `index.js` file upon execution.

### Building the App

Let's start creating the **robofriends** app!

#### Create `Card`

Create the `src/Card.js` file:

```jsx
import React from 'react';

const Card = () => {
    return (
        <div className='bg-light-green br3 pa3 ma2 grow bw2 shadow-5'>
            <img alt='robots' src={`https://robohash.org/${props.id}$200x200`} />
            <div>
                <h2>{props.name}</h2>
                <p>{props.email}</p>
            </div>
        </div>
    );
}

export default Card;
```

In which the `{props.id}`, `{props.name}` and `{props.email}` will take values from `index.js`.

Create the `robots.js` file:

```jsx

export const robots = [
    {
        id: 1,
        name: 'Leanne Graham',
        username: 'Bret',
        email: 'Sincere@april.biz'
    },
    {
        id: 2,
        name: 'Ervin Howell',
        username: 'Antonette',
        email: 'Shanna@melissa.tv'
    }
    ...
] 
```

Finally, modify the `src/index.js` file to display the cards:

```jsx
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import Card from './Card';
import registerServiceWorker from './registerServiceWorker';
import 'tachyons';
import { robots } from './robots'

ReactDoM.render(
        <div>
            <Card id={robots[0].id} name={robots[0].name} email={robots[0].email}/>
            <Card id={robots[1].id} name={robots[1].name} email={robots[1].email}/>
            <Card id={robots[2].id} name={robots[2].name} email={robots[2].email}/>
        </div>
    , document.getElementById('root'));

registerServiceWorker();
```

Note: the bracket around `robots` is to restructure it, which contains multiple objects.

#### Improve `Card`

Restructing `props` in `Card.js`:

```jsx
import React from 'react';

const Card = () => {
    const { name, email, id } = props; //restructuring
    return (
        <div className='bg-light-green br3 pa3 ma2 grow bw2 shadow-5'>
            <img alt='robots' src={`https://robohash.org/${id}$200x200`} />
            <div>
                <h2>{name}</h2>
                <p>{email}</p>
            </div>
        </div>
    );
}

export default Card;
```

Destructuring `props` in `Card.js`:

```jsx
import React from 'react';

const Card = ({ name, email, id }) => { //destructuring
    return (
        <div className='bg-light-green br3 pa3 ma2 grow bw2 shadow-5'>
            <img alt='robots' src={`https://robohash.org/${id}$200x200`} />
            <div>
                <h2>{name}</h2>
                <p>{email}</p>
            </div>
        </div>
    );
}

export default Card;
```

This is much cleaner than using `props.` separately.

#### Create `CardList`

Purpose: Instead of appending `Card` one by one in the `index.js` file, let's have a `CardList` component that helps us gather all the cards.

Create the `src/CardList.js` file:

```jsx
import React from 'react';
import Card from './Card';

const CardList = ({ robots }) => {
    return (
        <div>
            <Card id={robots[0].id} name={robots[0].name} email={robots[0].email}/>
            <Card id={robots[1].id} name={robots[1].name} email={robots[1].email}/>
            <Card id={robots[2].id} name={robots[2].name} email={robots[2].email}/>
        </div>
    )
}

export default CardList;
```

Modify the `src/index.js` file:

```jsx
...
ReactDoM.render(
        <CardList robots={robots}/>
    , document.getElementById('root'));
...
```

#### Improve `CardList`

Instead of adding the `Card` objects one by one to our `CardList` object, we may use loops to populate them.

In the `src/CardList.js` file:

```jsx
import React from 'react';
import Card from './Card';

const CardList = ({ robots }) => { //using map to loop through all the robots info and return a card object
    const cardArray = robots.map((user, i) = > {
        return (
        <Card
            key={i} //adding the key prop so react can keep track of the object changes more efficiently (instead of modifying the whole DOM)
            id={robots[i].id}
            name={robots[i].name}
            email={robots[i].email}
            />
        )
    })

    return (
        <div>
            { cardArray } // display the whole array
        </div>
    )
}
```

To make this even cleaner, we can just define the whole `cardArray` within `<div>`:

```jsx
import React from 'react';
import Card from './Card';

const CardList = ({ robots }) => {
    return (
        <div>
            {
                robots.map((user, i) = > {
                    return (
                    <Card
                        key={i}
                        id={robots[i].id}
                        name={robots[i].name}
                        email={robots[i].email}
                        />
                    )
                })
             }
        </div>
    )
}
```

#### Create `App`

Create `src/App.js`:

```jsx
import React from 'react';
import CardList from './CardList';
import SearchBox from './SearchBox';
import { robots } from './robots';

const App = () => {
    return (
        <div className='tc'>
            <h1>RoboFriends</h1>
            <SearchBox />
            <CardList robots={robots}/>
        </div>
    )
}

export default App;
```

Create `src/SearchBox.js`:

```jsx
import React from 'react';

const SearchBox = () => {
    return (
        <div className='pa2'>
            <input
                className='pa3 ba b--green bg-lightest-blue'
                type='search'
                placeholder='search robots'
            />
        </div>
    )
}

export default SearchBox;
```

#### Define the State

**State**: An object that describes your app. **Props** are simply things that come out of state.

So a parent feeds state into a child component and as soon as a child receives the state, it's a property that a child can never change.

To use state we need to change the `const` way to the  `react` way. So for example in `src/App.js`:

```jsx
import React, { Component } from 'react';
import CardList from './CardList';
import SearchBox from './SearchBox';
import { robots } from './robots';

class App extends Component {

    // define state
    constructor() {
        super()
        this.state = {
            robots: robots,
            searchfield: ''
        }
    }

    // access robots from state
    render() {
        return (
            <div className='tc'>
                <h1>RoboFriends</h1>
                <SearchBox />
                <CardList robots={this.state.robots}/>
            </div>
        )
    };
}

export default App;
```

#### Pass the Props to `SearchBox`

In `src/App.js`:

```jsx
import React, { Component } from 'react';
import CardList from './CardList';
import SearchBox from './SearchBox';
import { robots } from './robots';

class App extends Component {

    // define state
    constructor() {
        super()
        this.state = {
            robots: robots,
            searchfield: ''
        }
    }

    // print any change in the searchbox
    onSearchChange(event) {
        console.log(event.target.value)
    }

    // access robots from state
    // pass along the onSearchChange funciton to SearchBox
    render() {
        return (
            <div className='tc'>
                <h1>RoboFriends</h1>
                <SearchBox searchChange={onSearchChange}/>
                <CardList robots={this.state.robots}/>
            </div>
        )
    };
}

export default App;
```

In `src/SearchBox.js`:

```jsx
import React from 'react';

const SearchBox = ({ searchField, searchChange }) => {
    return (
        <div className='pa2'>
            <input
                className='pa3 ba b--green bg-lightest-blue'
                type='search'
                placeholder='search robots'
                onChange={searchChange}
            />
        </div>
    )
}

export default SearchBox;
```

#### Filter the Bots

In `src/App.js`:

```jsx
import React, { Component } from 'react';
import CardList from './CardList';
import SearchBox from './SearchBox';
import { robots } from './robots';

class App extends Component {

    // define state
    constructor() {
        super()
        this.state = {
            robots: robots,
            searchField: ''
        }
    }

    // filter the robots in state based on searchField
    // use the object = (props) => syntax to prevent errors
    onSearchChange = (event) => {
        this.setState({ searchField: event.target.value})
        const filteredRobots = this.state.robots.filter(robot => {
            return robots.name.toLowerCase().includes(this.state.searchField.toLowerCase())
        })
        // console.log(event.target.value)
    }

    // access robots from state
    // pass along the onSearchChange funciton to SearchBox
    render() {
        return (
            <div className='tc'>
                <h1>RoboFriends</h1>
                <SearchBox searchChange={onSearchChange}/>
                <CardList robots={this.state.robots}/>
            </div>
        )
    };
}

export default App;
```

Finally, move the `filteredRobots` object inside `render()` so `CardList` has access to it:

```jsx
import React, { Component } from 'react';
import CardList from './CardList';
import SearchBox from './SearchBox';
import { robots } from './robots';

class App extends Component {

    // define state
    constructor() {
        super()
        this.state = {
            robots: robots,
            searchField: ''
        }
    }

    onSearchChange = (event) => {
        this.setState({ searchField: event.target.value})
    }

    // access robots from state
    // pass along the onSearchChange funciton to SearchBox
    render() {
        const filteredRobots = this.state.robots.filter(robot => {
            return robots.name.toLowerCase().includes(this.state.searchField.toLowerCase())
        })
        return (
            <div className='tc'>
                <h1>RoboFriends</h1>
                <SearchBox searchChange={onSearchChange}/>
                <CardList robots={filteredRobots}/>
            </div>
        )
    };
}

export default App;
```

So this is what happens among the components:

1. `App` creates a `state` object that communicates to Virtual DOM and defines the `onSearchChange` function that modifies the `state` whenever there's an event.
2. `SearchBox` would run `onSearchChange` whenever there's a change in the search box, which then keeps updating the `state`.
3. In `render()` the app can then use the latest state to generate a list of robots as `filteredRobots`.
4. Finally also within `render()`, `CardList` can use `filteredRobots` to generate `Card`. 

