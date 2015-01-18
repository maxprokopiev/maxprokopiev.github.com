---
layout: post
title: Releasing lein heroku-deploy
category: posts
comments: true
tag: clojure
---

Inspired by [Paratrooper][paratrooper] I've released simple plugin for leiningen to simplify you heroku deploys - [heroku-deploy][heroku-deploy].

Usage is just simple as running:

    lein heroku-deploy

This command will:

- Activating maintenance mode
- Push changes to Heroku
- Restart the application
- Deactivate maintenance mode
- Warm application instance by requesting home page url

5 commands in one :)

Of course, there are many things to do:

- Overriding default command flow and inject custom commands
- Output git push info by lines, not as a single line

Finally, I want to say, that leiningen is [well documented][lein] about how to write your own plugin and publish it to [clojars][clojars].

[paratrooper]: https://github.com/mattpolito/paratrooper
[heroku-deploy]: https://github.com/juggler/lein-heroku-deploy
[lein]: https://github.com/technomancy/leiningen/blob/master/doc/PLUGINS.md
[clojars]: https://clojars.org/
