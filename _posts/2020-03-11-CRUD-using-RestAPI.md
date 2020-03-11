---
layout: post
title:  "CRUD using REST API"
image:  '/assets/img/node.jpg'
tags:   RestAPI NodeJS ExpressJs MongoDB
---

An **API** is the Application programming interface. Actually, it is the set of rules that allows developer programmers to talk with each other. The developers create API on the server side and allows client to interact with each other.

**REST** stands for Representational State Transfer it is the way for two computers to communicate over HTTP in a similar way to web browsers and servers. It is the set of rules that developer follow while creating their APIs.

So, let's create our **Simple CRUD APIs using NodeJs, MongoDB, and ExpressJs**

Before diving into NodeJs, Express and MongoDB we need to familar with the ES6 concept of javaScript as well as knowledege about JSON will be assests.

And also you need to select you IDE there are several IDE like Visual Studio code, WebStrome, you can also code in Sublime text. Choose any IDE you are comfortable with. For this tutorial I am using **Visual Studio code.**

so let's start it.

First you need to have Node install on your system you can download from Node offical website.

Open your visual Studio Code and type command in your terminal
{% highlight javascript %}
npm init -y
{% endhighlight %}

Basically, npm init is used to set up a new or existing npm package. For a default configuration I am using -y. And creates a _package.json file_ which consists of dependencies which we will discuss later on.

Now we will install our Express Framework and Mongoose, so type this command in your terminal
{% highlight javascript %}
npm i mongoose express 
{% endhighlight %}

where i stands for install. This add dependency to your _package.json file_ with version number. After installing you can see the **node_modules** appear in your project. Basically, a modules in Node.js is a a simple or complex functionality organized in single or multiple javascript files which can be reused throughout the Node.js application.

Now, create index.js file the file name must be index.js because when while using npm init -y we are given the default configuration.

![index](./assets/img/index.PNG);



