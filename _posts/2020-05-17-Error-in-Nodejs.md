---
layout: post
title:  "Error Mostly occurs in Node js "
image:  '/assets/img/error/error.jpg'
tags:   NodeJS, Express, Errors
---

While developing `node.js` application I had faced this issue multiple times. 

{% highlight Javascript%}
Error [ERR_HTTP_HEADERS_SENT]: Cannot set headers after they are sent to the client
{% endhighlight %}

After searching the problem in `Stackoverflow` I found that most of the `node.js` developer have faced same issues. 

So, I tried to fix this issues of my own, and I am suprised that it's solution is quite easy. 

`Error [ERR_HTTP_HEADERS_SENT]` is an `error` that is fired up when server tries to send more than one response to the client. 

so let us look a  simple code 

{% highlight Javascript%}

const express = require('express');
const bodyParser = require('body-parser');
const app = express();

app.use(bodyParser.json());
app.use(bodyParser.urlencoded({extended: false}));

app.post('/login', (req, res) => {
  if (!req.body.name) {
    res.status(400).json({
      status: 'error'
    });
  }

  res.status(200).json({
    status: 'succes'
  });

});

app.listen(4000, () => {
  console.log('Server running');
});

{% endhighlight %}

this is the simple `POST` request to a `/login` route using the express `framework`. Server should respond `404 Bad response` to the client if the request doesn't have `req.body`. Here, the request handler function already sent a response to the client using the `res.json()` method.

To fix this error 

The simple fix of this error is to add `return` statement to the response being sent from the if condition. The `return` statement ends function execution and specifies a value to be returned to the function caller.

{% highlight Javascript%}

const express = require('express');
const bodyParser = require('body-parser');
const app = express();

app.use(bodyParser.json());
app.use(bodyParser.urlencoded({extended: false}));

app.post('/login', (req, res) => {
  if (!req.body.name) {
    return res.status(400).json({
      status: 'error'
    });
  }

  res.status(200).json({
    status: 'succes'
  })
});
app.listen(4000, () => {
  console.log('Server running ');
});

{% endhighlight %}

When a client makes a server request to this endpoint('/login') with or without a request body to the server request, the server sends the correct response and stop the function execution as necessary.



