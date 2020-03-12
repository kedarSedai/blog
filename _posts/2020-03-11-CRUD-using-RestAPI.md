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

Now, create index.js file the file name must be index.js because while using npm init -y we are given the default configurations.
![]({{site.baseurl}}/assets/img/index.PNG)

you can see this "main" inside your _package.json file_ 

now inside your index.js file just write below code:
![]({{site.baseurl}}/assets/img/app.PNG)

Here, _express_ is the framework for Node.Js application and Mongoose provides a straight-forward, schema-based solution to model your application data. We install this two dependency you can see this in your _package.json file_ with version number.

This app starts a server and listens to server with the port number 3000. The app responds with Hello world! for request to the root URL (/) or route. For every other path like(/about),(/home) it will respond with 404 Not found. To run this application you need to type node index.js this will run your application and starts a server at port number 3000. But problem while using node index.js is that everytime when you make some changes in your appplicaion we need to restart the server this may be borring for the developers so we need to install nodemon what is does is it automatically run the server when we save changes in our code we don't need to restart the server it automatically restart the server.
_so, let's install nodemon first_
{% highlight javascript %}
npm i -g nodemon 
{% endhighlight %}
And nodemon will be installed globally to your system path.
{% highlight javascript %}
res.send();
{% endhighlight %}
Sending a response can be acheived by calling the res.send() method. The signature of this method lookes like res.send([body]). Where body can be any of the following: _Buffer_, _String_, _Object_ and an _Array_.

Now let us create setup Folder this will be the folder where we keep our secret keys for security purpose. And inside that(setup) folder create keys.js. So after creating this we will get the folder Structure like this:
![]({{site.baseurl}}/assets/img/keys.PNG)

And inside keys.js file add this code

![]({{site.baseurl}}/assets/img/mongoose.PNG)
This url comes from the MongoDB Atlas you need to have an account in MongoDB.You can create account freely.

Now add this you your index.js file

{% highlight javascript %}
//import keys.js file
const db = require('./setup/keys').mydb_url;

//Establishing connection
mongoose
        .connect(db, ({useNewUrlParser:true, useUnifiedTopology: true}))
        .then(() => console.log('MongoDB connected 🙂' ))
        .catch(err => console.log(err));
{% endhighlight %}

now write _nodemon_ in your terminal and you might see MongoDB connected.

Congraz 🙂 you just connected your application to MongoDB.

Now, lets's create our _Schema_. Everything in a mongoose starts with a schema. Each schema maps with the mongoDB collection and defines the shape of the documents within that collection.

so let's create our model folder and inside model create _User.js file_ which will be our schema.
Actually, we are following MVC pattern where
 * M stands for **Model**
 * V stands for **View** and 
 * C stands for **Controller** 
 **M**odel represents a domain specific data and business logic in MVC architeture.

So, after creating model folder our folder structure will look like this.

![]({{site.baseurl}}/assets/img/model.PNG)

so inside _User.js_ add this code

![]({{site.baseurl}}/assets/img/user.PNG)
where we are creating a schema we have user with the property of name and description. It depends how you define your schama like if you are making a login application then it may have email, password. Now, we just create our schema with name and description and exporting this model. Name of the model can be anything but I write _user_you can choose any other name.

Now let us create our routes. **Routing** refers to how an application’s endpoints (URIs) respond to client requests. 
First, let's create routes folder and inside route folder crete userRoutes.js file
and add this code:
![]({{site.baseurl}}/assets/img/userRoute.PNG)

Now let's first install bodyParser what bodyParser actually does is parse incoming request bodies in a middleware before your handlers, available under then _req.body_ property.

install bodyParser same as we done before for express and mongoose 
{% highlight javascript %}
npm i body-parser
{% endhighlight %}

and import this dependency in your root application that is (index.js) file

now your code must look like this:
![]({{site.baseurl}}/assets/img/indexbody.PNG)

Now in our routes folder inside user.js we are importing our schema that we have created inside our model folder and adding our routes in user.js file. So now code will look like this: 
![]({{site.baseurl}}/assets/img/save.PNG)

we just created our first route with POST method means that the data send to the server with POST is stored in the request body of the HTTP request. _It is one of the most common HTTP methods._
{% highlight javascript %}
req.body.title
{% endhighlight %}
It comes from the userSchema. we have use _async_ and _await_.They are the extension of the promises. 
Here, we just create the instance of the document and save in the database. 

Now for deleting the user 
Deleting the user is trick method we just need to add id . it looks like 
![]({{site.baseurl}}/assets/img/delete.PNG)
{% highlight javascript %}
req.params
{% endhighlight %}
is used to define route with route parameters

For updating the user 
![]({{site.baseurl}}/assets/img/update.PNG)
here, we are updating user's title with the userId.

{% highlight javascript %}
remove(), updateOne() these all are the methods of mongoDB.
{% endhighlight %}

now inorder to get all data that is stored in database we just need to add GET route in our routes folder inside userRoutes.js file
and it looks like this:

![]({{site.baseurl}}/assets/img/getalldata.PNG)

we this we just created our simple **CRUD REST API** we the help of MONGODB, EXPRESS.JS AND NODE.JS 😍..

you can find this code at : [RestApi](https://github.com/kedarSedai/Restapi)