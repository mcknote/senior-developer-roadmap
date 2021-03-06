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

Key phases in short:

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

* *Render blocking*; need to make it as lightweight as possible
* Only load whatever is needed
* Incorporate above the fold loading
  * Only load what is being displayed
* Add media attributes
* Get less specificity

### JS

* *Parser blocking*
* Load scripts asynchronously
  * Use `<script async>`
  * Tell the browser to go ahead download scripts with another thread
  * Execute once the script is downloaded
  * The execution timing can be tricky and thus affect user experience (e.g. accessing a DOM element that is not loaded yet)
  * Tip: Add them to anything that doesn't affect the DOM or CSSOM, i.e. pretty much all external scripts that require no knowledge on our code
* Defer loading of scripts
  * Use `<script defer>`
  * Execute once the whole parsing is done
* Minimize DOM manipulation
* Avoid long running Javascript

#### Choice of `<script>` tags

* `<script>`
  * Critical app scripts
* `<script async>`
  * Third-party scripts that don't affect the DOM
  * If the core funcitonality requires javascript, **async** is the best
* `<script defer>`
  * Third-party scripts that don't affect the DOM and aren't important
  * If the core functionality doesn't requrie javascript, **defer** can be used

#### Resources: Async + Defer

* [The location of the script tags](https://stackoverflow.com/questions/10808109/script-tag-async-defer)

### Additional Resources

* [Optional: Resource Prefetching](https://css-tricks.com/prefetching-preloading-prebrowsing/)
* [Resources: HTTP/2](https://developers.google.com/web/fundamentals/performance/http2/)

#### Dev Tools

* [View main thread activities in a table](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference#activities) to sort activities based on which ones took up the most time.
* [Analyze frames per second (FPS)](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference#fps) to measure whether your animations truly run smoothly.
* [Monitor CPU usage, JS heap size, DOM nodes, layouts per second, and more](https://developers.google.com/web/updates/2017/11/devtools-release-notes#perf-monitor) in real-time with the Performance Monitor.
* [Capture screenshots while recording](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference#screenshots) to play back exactly how the page looked while the page loaded, or an animation fired, and so on.
* [View interactions](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference#interactions) to quickly identify what happened on a page after a user interacted with it.
* [Find scroll performance issues in real-time](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference#scrolling-performance-issues) by highlighting the page whenever a potentially problematic listener fires.
* [View paint events in real-time](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference#paint-flashing) to identify costly paint events that may be harming the performance of your animations.
* [View main thread activity](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference#main) to view every event that occurred on the main thread while you were recording.

#### Additional image manipulation tools

* [XNConvert](https://www.xnview.com/en/xnconvert/): This free, cross-platform tool can handle batched images, and performs resizing, optimization, and other transforms.
* [ImageOptim](https://imageoptim.com/mac): This free tool is available for Mac and as an online service, and is specifically aimed at optimizing images for speed, including metadata removal (discussed above).
* [ResizeIt](https://itunes.apple.com/us/app/resizeit/id416280139?mt=12): A Mac-only desktop product that lets you change the size of multiple images simultaneously, and can convert file formats at the same time.
* [PicResize](http://www.picresize.com/): One of several good browser-based tools that gives you lots of options for cropping, rotating, resizing, adding effects to, and converting images.
* [Gimp](https://www.gimp.org/): This ever-popular cross-platform tool just gets better with age. Powerful and flexible, Gimp lets you perform a wide variety of image manipulation tasks including, of course, resizing.

## Exercise

### #1 - Media Queries

* [VIEW AND REMOVE EXIF ONLINE](https://www.verexif.com/en/)
* [Media Queries](https://css-tricks.com/snippets/css/media-queries-for-standard-devices/)
* [Media Queries Cheat Sheet](http://www.bsidestudios.com/blog/media-queries-common-sizes-cheat-sheet)

### #2 - Network Optimizations

### #3 - Critical Render Path

### #4 - Keiko Corp Website

**[Project repository](https://github.com/aneagoie/keiko-corp)**

Performance testing sites:
* [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)
* [WebPageTest](https://www.webpagetest.org)

#### Obvious issues

* Too many separate `css` and `js` files loaded in the `html` file
* The `<script>` tag has been placed before `</head>`
* The image sizes are generally too big
* Too many reqeusts
* Didn't use above-the-fold-loading technique
* Using too much jQuery; *[You might not need jQuery](http://youmightnotneedjquery.com)*

