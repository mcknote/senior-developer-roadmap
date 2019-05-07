# Performance Part 1

## Introduction

* Performance is very very important; the slower the website the more loss it creates.
* Client-server relationship

## Three Keys to Performance

* Client site
* Transfer
* Backend processing

**IMPORTANT**: There are infinite ways to improve website performance, but we want to think like a senior developer — *Focus on the problem and solve the problem in the most efficient and valuable way*.

So we are going to focus on the big ticket item that will solve 90% of the problem first.

### Topics

* Client site
  * Ctirical Render Path
  * Optimized Code
  * Progressive Web App
* Transfer
  * Minimize Files
  * Minimize Delivery
* Backend processing
  * CDNs
  * Caching
  * Load Balancing
  * GZIP
  * DB Scaling

## Network Performance

Two main things to do:

* Honey I shrunk the files
  * Minimize text
  * Minimize images
* The traveling deliveryman

### Honey I shrunk the files

#### Minimize text

* Remove spaces
* Use shorter variable names
* Use uglify functions (e.g. `minify-js`) to perform these actions automatically

#### Minimize images

* Follow general advice
  * Choose simple illustrations over highly detailed photographs
  * Resize the image based on its display size
    * Use media queries; browsers won't download resources that don't fit the query
  * Use CDNs like imigx
  * Remove image metadata
* Pick the right format for best performance
  * JPG
    * colorful
    * use [JPEG-optimizer](http://www.jpeg-optimizer.com)
    * always lower image quality (30%-60%)
  * SVG
    * simple icon
  * PNG
    * transparency
    * use [TinyPNG](https://tinypng.com)
  * GIF
    * animations

### The traveling deliveryman

* Limit the number of files we deliver
* Bundling through tools like [webpack](https://webpack.js.org)
* [Max Parallel Requests Per Browser](https://stackoverflow.com/questions/985431/max-parallel-http-connections-in-a-browser)

## Critical Render Path Introduction

What browser does under the hood:

1. Requests HTML file
2. Constructs document object model (DOM), which describes the web content
3. Requests CSS file(s)
4. Gets back to the DOM structure
5. Constructs CSS object model (CSSOM)
6. Requests JS file(s)
7. Applied JS to both the DOM and the CSSOM and completes all the changes
8. Combines the DOM and the CSSOM into a render tree
9. Uses the render tree to figure out the layout
10. Displays the webpage

In short:

1. DOM
2. CSSOM
3. Render Tree
4. Layout
5. Paint

## Optimizing Critical Render Path

### HTML

* Load CSS as soon as possible (in the `<head>`) to create CSSOM
* Load JS as late as possible (right before `<body>`), because it requires both CSS and HTML to be ready to get started; also to prevent stalling CSS elements

### CSS

* Render blocking; need to make it as lightweight as possible
* Only load whatever is needed
* Incorporate above the fold loading
  * Only load what is being displayed
* Add media attributes
* Get less specificity

### JS

* Load scripts asynchronously
* Defer loading of scripts
* Minimize DOM manipulation
* Avoid long running Javascript

## Exercise

### #1 - Media Queries

* [VIEW AND REMOVE EXIF ONLINE](https://www.verexif.com/en/)
* [Media Queries](https://css-tricks.com/snippets/css/media-queries-for-standard-devices/)
* [Media Queries Cheat Sheet](http://www.bsidestudios.com/blog/media-queries-common-sizes-cheat-sheet)

### #2 - Network Optimizations
