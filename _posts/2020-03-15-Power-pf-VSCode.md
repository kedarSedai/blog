---
layout: post
title:  "🔥Power of VS Code"
image:  '/assets/img/vscode/vscode.png'
tags:   VS code
---

**Visual Studio Code (VS Code)** is a code editior that is used for building and debugging modern web and cloud applications. 
There are several code editior like _Sublime Text_, _Nodepad++_, _Atom_, _Brackets_, _Vim_, _TextMate_. Due to rich content and in-built extensions like _Emmet_ **VS** code is gaining its importance among the developers. 
Let us talk about **Emmet** 

Visual Studio supports Emmet. No any extension is required. Emmet abbrevation are enabled by default in _html_, _pug_, _jsx_, _css_, _scss_, _xml_ files. 

Emmet can be used in _.html_ files like 
{% highlight Emmet %}
h1.head and enter tab
{% endhighlight %}
It will create h1 tag with className head and if you replace _._ with _#_ then you will get _id_. Same goes for all HTML tags like _p_, _table_, _ul_, _li_🤨.

For _ordered list_ and _unorderd list_ 
{% highlight Emmet %}
ul>li*3 
{% endhighlight %}
It will create unorderlist with _3_ list items **you need to enter tab after** _ul>li*3_

**lorem ipsum generator**
just type lorem and enter tab
{% highlight Emmet %}
lorem
{% endhighlight %}
If you want only 3 word then type _lorem3_ and enter tab -->
{% highlight Emmet %}
ul.emoji>lorem3.item*4
{% endhighlight %}
will output as

![]({{site.baseurl}}/assets/img/vscode/img.PNG)

{% highlight Emmet %}
div+p+h1
{% endhighlight %}
will output as

![]({{site.baseurl}}/assets/img/vscode/div.PNG)

{% highlight Emmet %}
a{click me}
{% endhighlight %}

will output as

![]({{site.baseurl}}/assets/img/vscode/click.PNG)

**Emoji extension**

First, you need to install Emoji Snippets Extension in your VS code. So. after instlling you are able to use Emoji. Inorder to use emojis you need to type _:(colon)_ 

To insert emoji in your h1 tag you just simply need to write
{% highlight Emmet %}
<h1>name:</h1>
{% endhighlight %}

