---
layout: post
title:  "Read and Parse JSON asynchronously "
image:  '/assets/img/jsonimg/json.png'
tags:   NodeJS, JSON
---

`JSON` stands for `JavaScript Object Notation`. `JSON` is syntax for storing and exchanging data. It is a text, written with JavaScript Object Notation. 

`JavaScript` can `parse` `JSON` file  synchronously and asynchronously. The problem with using synchronous is when used in a webServer where all the requests will become blocked while the synchronous file read is running. For, this reason we generally use `async` version of the `fs` function in our code. 

Accessing files in the NodeJS is done with the `native module fs` write gives you the functionality of read, write, along with many other tools. Because it is native module we do not need to dowload and install like other module we can simply import it as

{% highlight Javascript%}
const fs  = require('fs');
{% endhighlight %}

This is our JSON file 'todos.json'
{% highlight JSON %}
   {
    "todos": [
        {
            "id": 1,
            "text": "task number 1",
            "priority": 3,
            "done": false
        },
        {
            "id": 2,
            "text": "task number 2",
            "priority": 3,
            "done": false
        },
        {
            "id": 3,
            "text": "task number 3",
            "priority": 3,
            "done": false
        } 
    ]
}
{% endhighlight %}

So, to read the `JSON` file 

{% highlight Javascript %}
const fs  = require('fs');
    fs.readFile('todos/json', 'utf8', (err, data) => {
        if(err) {
            console.log('Error While Reading JSON file', err);
        }else{
            console.log('File Read', data)
        }
    });
{% endhighlight %}

`todos.json` is the relative path of our json file. _utf8_ is optional parameters for encoding the file that we are reading. and `(err, data) => {}` is the `callback function` that runs after the file has been read.

After having the concept of reading the `JSON` file here is the complete example of parsing the `JSON` file

{% highlight JSON %}
const fs = require('fs');

app.get('/todos', (req, res) => {

    fs.readFile('todos.json', 'utf-8', (err, data) => {
        if(err) {
            console.log('Error Occured', err)
        }
        try{
            const todos = JSON.parse(data);
            console.log('JSON parsed' + todos.todos[0].text);
            res.send('JSON Parsed ' +  todos.todos.map(todo => todo.done))
        }catch(err) {
            console.log('Error from catch Block', err );
        }
    });
});
{% endhighlight %}

Using the `data` from reading `todos.json` we create an object now we can access the property from the JSON. `JSON.parse` can throws an exception errors and halt our program if any invalid `JSON` string is passed so, such type of exception are caught in `catch` block. 

`todos.todos.[0].text` returns the property(text) from the first array of objects
`todos.todos.map(todo => todo.done)` returns the property(done) form all array of objects.


