---
layout: post
title:  "Terminal Commands"
date:   2020-04-24 00:44:42 -0700
categories: thoughts
tags: [terminal, commands]
author: "Brandon"
---

<b>Jekyll</b>

Hosting Local Server:
{% highlight ruby%}
exec bundle serve jekyll serve
exec bundle serve jekyll serve --drafts
{% endhighlight %}

Pushing to Github:
{% highlight ruby%}
git status
git add .
git commit -m "initial commit"
git push origin gh-pages
{% endhighlight %}
