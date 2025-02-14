---
layout: post
title:  "Use ExpressJs to render HTML Files"
image:  '/assets/img/express/node.PNG'
tags:   ExpressJs, HTML, NodeJs
---

In _NodeJs_ as well as in _ExpressJs_ application there is a simple way of sending _HTML_ or other type of file `res.sendFile()`.

**Using res.sendFile()**

Inorder to use `res.sendFile()` we need to pass in a path to the file. `Path` is used for _handling_ and _transforming_ file paths. This module can be imported by using the syntax like `const path = require('path')`.

So, Here is the example of using res.sendFile() to send a _HTML_ file

This is our _server.js_ file

![]({{site.baseurl}}/assets/img/express/html.PNG)

For this first, you need to install dependencies like
`npm i express`

_index.html_ will look like
 ![]({{site.baseurl}}/assets/img/express/index.PNG)

and can run on the server by writing command `node server.js`
