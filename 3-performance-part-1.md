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

Minimize text

* Remove spaces
* Use shorter variable names
* Use uglify functions to perform these actions automatically

Minimize images

* Follow general advice
  * Choose simple illustrations over highly detailed photographs
  * Resize the image based on its display size
  * Use CDNs like imigx
  * Remove image metadata
* Pick the right format for best performance
  * JPG
    * colorful
    * use JPEG-optimizer
    * always lower image quality (30%-60%)
  * SVG
    * simple icon
  * PNG
    * transparency
    * use TinyPNG
  * GIF
    * animations

