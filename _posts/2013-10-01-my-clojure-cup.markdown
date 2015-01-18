---
layout: post
title: My Clojure Cup 2013
category: posts
comments: true
tag: clojure
---

Last weekend I attended [Clojure Cup 2013][clojurecup]. Initially, I submitted my entry as a twitter mashup where users could create a dashboard based on service statuses (status is determined from a service's twitter account, e.g. [@heroku_status][heroku_status]).

But everything I did during this contest is writing Chef and Capistrano recipes for Clojure deployment.

On the one hand it's caused by the lack of time to participate for the following reason:

<blockquote class="twitter-tweet"><p>I&#39;m getting married next week, but still attending <a href="https://twitter.com/clojurecup">@clojurecup</a>, what&#39;s your excuse? :)</p>&mdash; Max Prokopiev (@mprokopiev) <a href="https://twitter.com/mprokopiev/statuses/383980626132475904">September 28, 2013</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

On the other – by the lack of resources describing Clojure deployment on VPS like DigitalOcean.

There is a great article about [Manual Clojure Deployment][juxt_article] by [JUXT][juxt] team. But (as you may have already noticed) it describes __manual__ Clojure deployment. Come on guys, it's 2013, there are tools like Puppet and Chef to handle that. This is what I thought reading this article. So my Clojure Cup entry quickly mutated to ["Automated Clojure Deployment"][app].

I've picked initial Chef config from our [chef template][rails3-base-chef] which we are using at [FlatStack][flatstack] to prepare servers for deployment rails apps.

What I've done so far:

- recipe to set up `clojurecup` user (this was a requirement)
- recipe to set up nginx config (as described in JUXT's article) which works as a reverse proxy for the jetty server, serves static pages and caches content
- jdk7
- latest stable [leniningen][lein]

Also I've created a simple [Capistrano][cap] recipe. With task to start/stop/check and restart [lein daemon][lein-daemon] (which I'm using to start an app server)

Today I'll put my code to github with detailed readme. Keep in touch :)

__P.S.__

It was __fun__! Thanks to [Tero Parviainen][teropa] and team.

During development I've made two pull requests to [lein-daemon][lein-daemon-pr] and [chef-leiningen][chef-leiningen-pr]. If anyone who reading this article have access to review and merge them - please do that &#8743;&#8743;"


[clojurecup]: http://clojurecup.com/
[heroku_status]: https://twitter.com/heroku_status
[digital_ocean]: https://www.digitalocean.com
[juxt]: https://juxt.pro/index.html
[juxt_article]: https://juxt.pro/articles/manual-clojure-deployment.html
[rails3-base-chef]: https://github.com/fs/rails3-base-chef
[flatstack]: http://www.flatstack.com/
[lein-daemon]: https://github.com/juggler/lein-daemon
[chef-lein]: https://github.com/juggler/chef-leiningen
[lein]: http://leiningen.org/
[cap]: https://github.com/capistrano/capistrano
[lein-daemon-pr]: https://github.com/arohner/lein-daemon/pull/18
[chef-leiningen-pr]: https://github.com/runa-labs/chef-leiningen/pull/3
[app]: http://clojurecup.com/app.html?app=wtf
[teropa]: https://twitter.com/teropa
