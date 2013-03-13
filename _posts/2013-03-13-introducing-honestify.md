---

date: 2013-03-13
layout: post
title: |
  Introducing Honestify
# published: false
categories:
  - Web
excerpt: |
  For a while, I've been curious about learning to build <a href="http://en.wikipedia.org/wiki/Bookmarklet">bookmarklets</a> and browser plugins. I figured that it couldn't be too difficult, but I didn't really have anything particular to build. So it just sat in the back of my mind until I saw a <a href="https://twitter.com/ethanschoonover/status/293914120741335041">tweet</a> by <a href="https://twitter.com/ethanschoonover">Ethan Schoonover</a>. While I know that he was just joking, it seemed like a perfect excuse to take to learning something new.

---

For a while, I've been curious about learning to build [bookmarklets](http://en.wikipedia.org/wiki/Bookmarklet) and browser plugins. I figured that it couldn't be too difficult, but I didn't really have anything particular to build. So it just sat in the back of my mind until I saw a [tweet](https://twitter.com/ethanschoonover/status/293914120741335041) by [Ethan Schoonover ](https://twitter.com/ethanschoonover).

<blockquote class="twitter-tweet"><p>I'd like a browser plugin that auto-translates "more from around the web" to "scammy link bait we get money for".</p>&mdash; Ethan Schoonover (@ethanschoonover) <a href="https://twitter.com/ethanschoonover/status/293914120741335041">January 23, 2013</a></blockquote>

While I know that he was just joking, it seemed like a perfect excuse to take to learning something new. So I started googling. As that was happening, I saw a [post](http://frankchimero.com/blog/2013/02/there-isnt-an-app-for-that-and-this-is-terribly-disappointing/) by [Frank Chimero](https://twitter.com/fchimero) in which he suggested that we need a 

> Browser plugin that finds each instance of the word “troll” and replaces it with “asshole.”

That fit in quite nicely with the search and replace plugin that I was building so I decided to build it in such a way that I could easily add new words and phrases to be replaced. Once that was done, I threw together a quick [landing page](http://honestify.com).

I wrapped it all up and called it [Honestify](http://honestify.com). Right now it is only available for Chrome. I also made a bookmarklet, for those who might be interested, but don't want to install a browser plugin. So far it just replaces those two phrases, but I have it pulling from [Github](https://github.com/bryanstedman/honestify) so if you would like to add something then open an issue, or better yet send me a pull request. 

Down the line, I'd like to add a few more features, like being able to toggle it on and off without having to disable the whole plugin and optional highlighting of words that have been changed. For now, feel free to give it a go. You can get it at [honestify.com](http://honestify.com). Let me know what you think and hit me up on [Github](https://github.com/bryanstedman/honestify) if you find any bugs or want to add anything.