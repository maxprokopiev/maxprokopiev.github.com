---
layout: post
title: Diving Into Clojure
category: posts
comments: true
---

In a past few months I've started playing with [Clojure][clojure]. There are many reasons for that. Currently I'm working with ruby at [Flatstack][flatstack]. Actually, I work mostly with rails and this is already bored me. Not so much ruby, but the rails thing - when working with rails I've started to forget basic things and (which is even worse) stopped looking at how things really work . For example, why should I care how to rewrite this simple query in MongoDB console:

{% highlight ruby %}
  Article.where(title: 'Clojure').order(:published_at.desc)
{% endhighlight %}

Rails will do that for me. You should only care about logic specific to your domain. And this is super cool! ...if you want to build websites all your life. I want more hardcore programming like writing mongodb adapter or wrapper for [Titan][titan].

So I started to look for other programming languages. I have been passively fond of functional programming languages. Tried scheme, erlang and even haskell. But there was one language which interested me the most - Clojure. So I thought to myself why not to try it. I'm not afraid of parentheses, interested in how JVM works, love FP.

I've started to read [SICP][sicp] and try to solve exersices with clojure. Then I've reached the web - ring, compojure, hiccup and clojurescript. Ring is like Rack, compojure is clojure's sinatra - not so much difficult.

Now I want to organize all of this in my head. So I decided to start this blog.

---

If you have an interesting clojure project and looking for a good developer to work with - ping me on Twitter - I'm [@mprokopiev][twitter].

[clojure]: http://clojure.org
[flatstack]: http://www.flatstack.com
[titan]: http://thinkaurelius.github.com/titan/
[sicp]: http://mitpress.mit.edu/sicp/full-text/book/book.html
[twitter]: http://twitter.com/mprokopiev
