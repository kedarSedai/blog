---
layout: post
title:  "Read and Parse JSON asynchronously "
image:  '/assets/img/jsonimg/json.png'
tags:   NodeJS, JSON
---

`JSON` stands for `JavaScript Object Notation`. `JSON` is syntax for storing and exchanging data. It is a text, written with JavaScript Object Notation. 

`JavaScript` can `parse` `JSON` file  synchronously and asynchronously. The problem with using synchronous is when used in a webServer where all the requests will become blocked while the synchronous file read is running. For, this reason we generally use `async` version of the `fs` function in our code. 