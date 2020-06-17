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
  console.log('Server live');
});

{% endhighlight %}

