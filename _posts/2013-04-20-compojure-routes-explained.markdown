---
layout: post
title: Compojure routes explained
category: posts
comments: true
tag: clojure
---

If you don't know what Compojure is then you should go [here][compojure]. In this post I'll try to explain how Compojure generates routes and how can you get a request data via destructuring.

### defroutes

{% highlight clojure %}
  (defroutes app
    (GET "/posts" [] {params :params}
      (fetch-posts params))
    (POST "/posts" [] {params :params}
      (create-post params))
    (route/not-found "Not Found"))
{% endhighlight %}

### Destructuring

### ring-mock

[compojure]: https://github.com/weavejester/compojure/
