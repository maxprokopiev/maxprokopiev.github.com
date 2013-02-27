First of all I should say that ClojureScript is great tool for writing single page applications with complex client-side logic (take a look at [prismatic][prismatic] they use it). Another great feature of ClojureScript is that you can [re-use you server-side clojure code][sharing] in your scripts.

But in this post I want to list some small disadvantages, things that uncomfortable for when I write code in ClojureScript

But here I want to list things which made

Logging

Remember old good console.log:

console.log('Hello world');

Which looks more cleaner in CoffeeScript:

console.log 'Hello world'

Now look at ClojureScript's version:

(.log js/console "Hello world")

You can search github and you'll find code like this:

(defn log [obj]
    (.log js/console (pr-str obj)))

or this:

(defn log [& more]
  (.log js/console (apply str more)))

People don't like to be typewriters :)

JavaScript objects

Every time you want to interact with js objects you need to use js-obj construct:

(js-obj "foo" 1 "bar" 2)

So to send some json to server you'll need:

(send-to-server (.stringify js/JSON (js-obj "foo" bar)))

I'm in search for good clojure map -> js object conversion macro. Again, people end up with helper functions to make this conversion:

(defn clj->js
  "makes a javascript map from a clojure one"
  [cljmap]
  (let [out (js-obj)]
    (doall (map #(aset out (name (first %)) (second %)) cljmap))
    out))
<script src="https://gist.github.com/lynaghk/1141054.js"></script></script>
https://github.com/asmyczek/js-clojure-bridge/blob/master/src/cljrt.clj#L134

Seems like there is an issue for that on [clojure's JIRA][http://dev.clojure.org/jira/browse/CLJS-37]

All these I've experienced during conversion of chat-websocket js scripts.

Not good for small utility scripts because of the runtime
