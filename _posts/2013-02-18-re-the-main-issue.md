---

date: 2013-02-18
layout: post
title: |
  RE: The main issue
categories:
  - html
  - W3C
  - Tech
  - Web
excerpt: |
  A couple weeks ago <a href="https://twitter.com/adactio/">Jeremy Keith</a> wrote <a href="http://adactio.com/journal/6014/">a post</a> about the new main element that is <a href="http://www.w3.org/html/wg/drafts/html/master/grouping-content.html#the-main-element">making its way into the WC3 spec</a> and I have been meaning to jot down my thoughts ever since. First off, I am a big fan of Jeremy Keith. He is a very smart guy and find myself having to think twice when I find our views differ, but in the spirit of keeping the discussion going I will press on.

---


A couple weeks ago [Jeremy Keith](https://twitter.com/adactio/) wrote [a post](http://adactio.com/journal/6014/) about the new `main` element that is [making its way into the WC3 spec](http://www.w3.org/html/wg/drafts/html/master/grouping-content.html#the-main-element) and I have been meaning to jot down my thoughts ever since.

First off, I am a big fan of Jeremy Keith. He is a very smart guy and find myself having to think twice when I find our views differ, but in the spirit of keeping the discussion going I will press on.

In his [original post](http://adactio.com/journal/6014/), Jeremy Keith raises concerns about how the `main` element is being implemented. Specifically he is questioning why it scopes to the body of the document and thus can only be used a maximum of one time. I’ll let you read his post as he will have said it more elegantly that I will. Go on… I’ll wait.

Okay, so I actually had the same concerns when I first read the spec. As soon as I came to the sentence “Authors must not include more than one [main](http://www.w3.org/html/wg/drafts/html/master/grouping-content.html#the-main-element) element in a document.”, I thought that [it seemed like an unnecessary addition](https://twitter.com/bryanstedman/statuses/282685499074805760). “Why would we add a shiny new element and then immediately cripple it’s usefulness?”,  I thought. But I have since come around on the issue and now support the spec as written.

As a side note, Jeremy says that he believes that the `head` and `body` tags were the only other elements that can be used zero or one time. I feel compelled to point out (because us web folk get a sick sort of satisfaction out of talking about semantics and specs) that the [`base`](http://www.w3.org/html/wg/drafts/html/master/document-metadata.html#the-base-element) tag also falls into this category. In all fairness, `base` tags are weird and _almost_ don’t count.

Anyway, one of the big reasons that I changed my mind is accessibility. You see, the `main` element is supposed to map to the ARIA role with the same name. This will help assistive technologies such as screen readers better maneuver the page content. Jeremy does mention this, but also suggests that it would be easy enough to take the `main` element that scopes to the body tag and just assign that one the ARIA role of main. I can see what he is getting at, and there certainly are examples of elements working this way in the spec, but I feel like this diminishes the need for a `main` element. As soon as we start using formulas to determine which element really is the main `main` element then we might as well do away with `main` and just use the awesomely named [Scooby Doo algorithm](http://www.brucelawson.co.uk/2012/scooby-doo-content-element/)   Basically, if we are making computers figured it out anyway, why even use a `main` element?

The second reason that I support the spec as written is that I see a slight difference in the purpose and meanings behind the `main` element and the others that Jeremy compares it to, namely the `header` and `footer`. This difference is not based on anything in the spec but the way that I think of the words, so take it with a grain of salt, but it is this: `header` and `footer` deal with formatting and sectioning where as `main` deals with content. When I first started to come around to the idea of this new element one of the first use cases I thought of after assistive technologies was [Instapaper](http://www.instapaper.com/). Instapaper (and other services like it) strip the main content of a page out for later reading. Most of the time it does a great job finding just the part of the page that I am interested in and I get a great reading experience with just the main article and no navigation, ads, etc. Most of the time. Occasionally I end up with content from an ad or half of the site navigation and the article has been overlooked. Having a way for authors to specifically specify which content is the main content would be great for that.

Also as a last thought regarding accessibility,  I am not an expert when it comes to web accessibility but I do try to stay informed. Thanks to [Dave Rupert](https://twitter.com/davatron5000) and friends we have a great new, community run resource in [A11YProject.com](http://bryanstedman.com/blog/2013/02/re-the-main-issue/A11YProject.com) I even have a couple commits in there some where. But I think that the assisted technology (screen readers, etc. ) are slower to incorporate innovations and new fancy HTML tags so, for the time being at least, I would recommend that you continue to explicitly set ARIA roles even on elements that should map to them, even as much as `<main role="main">` kind of hurts my eyes.

Anyway, give me a call Jeremy and we can hash this out.