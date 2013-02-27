---
layout: post
title: Trying ClojureScript
category: posts
comments: true
tag: clojure
---

First of all I should say that [ClojureScript][cs] is a great tool for writing single page applications with complex client-side logic (take a look at [prismatic][prismatic], they use it). Another great feature of ClojureScript is that you can [re-use you server-side clojure code][sharing] in your scripts.

But here I want to list some small disadvantages, things that I found uncomfortable while trying ClojureScript.

## Logging

Remember old good console.log:

{% highlight javascript %}
  console.log('Hello world');
{% endhighlight %}

Which looks more cleaner in CoffeeScript:

{% highlight coffeescript %}
  console.log 'Hello world'
{% endhighlight %}

Now look at ClojureScript's version:

{% highlight clojure %}
  (.log js/console "Hello world")
{% endhighlight %}

You can search github and you'll find code like this:

{% highlight clojure %}
  (defn log [obj]
      (.log js/console (pr-str obj)))
{% endhighlight %}

or this:

{% highlight clojure %}
  (defn log [& more]
    (.log js/console (apply str more)))
{% endhighlight %}

People don't like to be typewriters :)

## JavaScript objects

Every time you want to interact with js objects you need to use js-obj construct:

{% highlight clojure %}
  (js-obj "foo" 1 "bar" 2)
{% endhighlight %}

For example to send some json to server you'll need:

{% highlight clojure %}
  (send-to-server (.stringify js/JSON (js-obj "foo" bar)))
{% endhighlight %}

Again people end up with helper functions for clojure map -> js object conversion:

{% highlight clojure %}
  (defn clj->js
    "makes a javascript map from a clojure one"
    [cljmap]
    (let [out (js-obj)]
      (doall (map #(aset out (name (first %)) (second %)) cljmap))
      out))
{% endhighlight %}

<script src="https://gist.github.com/lynaghk/1141054.js"></script></script>

Seems like there is an issue for that in [clojure's JIRA][jira].

## Debugging

Sometimes ClosureScript compiler crashes with NullPointerException and without ANY line number. It is very difficult when you need to comment lines to guess which one is failing.

---

All of these I've experienced during [conversion][cljs] of [chat-websocket][chat] js scripts to ClojureScript. I think that ClojureScript is not good for small utility scripts because of the runtime and  necessity for helper functions. Next time when I need to write some simple frontend code I'll use CoffeeScript. But I'm still learning and trying cljs, so there will be other posts about it.

[cs]: https://github.com/clojure/clojurescript
[prismatic]: http://blog.getprismatic.com/ 
[sharing]: https://github.com/emezeske/lein-cljsbuild/blob/0.3.0/doc/CROSSOVERS.md
[jira]: http://dev.clojure.org/jira/browse/CLJS-37
[cljs]: https://github.com/http-kit/chat-websocket/blob/master/src-cljs/main.cljs
[chat]: https://github.com/http-kit/chat-websocket/
