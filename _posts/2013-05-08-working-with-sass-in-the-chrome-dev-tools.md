---
layout: post
title:  "Working with Sass in the Chrome dev tools"
date:   2013-06-08
categories: sass css chrome web development
---

Working with [Sass](http://sass-lang.com) has lots of upside, but one of the frustrations that I had was in debugging my Sass stylesheets. I was used to cracking open the Chrome dev tools and seeing exactly where in my CSS styles were being called. With Sass all of the styles come from a generated CSS file that I had never looked and and would never be editing directly. Luckily, we can upgrade this situation.

## Debug Info to the Rescue - (deprecated)
Turning on debug info allows us to see which Sass file styles in our CSS are coming from, hooray! But the process of getting that set up feels a bit like you need to be part of a special club and know the secret handshake. Well, I am here to induct you into this club. Right this way…

### Get Chrome on Board
The first thing that we need to do is enable Developer Tools experiments in Chrome. To do this point your browser to [chrome://flags/#enable-devtools-experiments](chrome://flags/#enable-devtools-experiments). Chrome://flags is a magical land where Google hides experimental features. Adding the '#enable-devtools-experiments' hash at the end will take you towards the bottom-ish of the page to a row called "Enable Developer Tools Experiments". Hit the "enable" and then restart Chrome. They even give you a handy "Relaunch Now" button at the bottom.

Great that's step one sorted. Now open up the dev tools and find the settings cog in the bottom right (or hit the “?” for keyboard shortcut bonus points). When you click that you will now have a third option on the left called "Experiments". Hit that, find and check the "Support for Sass" box. Now we will close the dev tool for the time being.

### Project settings
Now that the browser is all set up, let's move on to project settings. If you, like me, use [compass](http://compass-style.org/) with your Sass projects then the setting go in your config.rb file. First add the line `sass_options = {:debug_info => true}`. Next make sure that your `output_style` is set for anything other than `:compressed` and that you don't set `line_comments`. Now that that's all set, run a quick compile so that these changes are reflected in your CSS. Sometimes, just to be safe, I'll delete the CSS file to be extra sure that Sass generates a brand new file with my new settings. If you run into any issues, give that a try. 

### What just happened?
If you look in your CSS file now you will notice it is littered with nonstandard media queries. They are not really human readable, but you will notice that they include the full path to your Sass files.

### Inspecting
Ok we can finally get into the dev tools. Give both your page and the dev tools a refresh if they are open. Now, when you inspect an element, the styles will show both the file name and line number of the sass file that set that style. You can play with the styling and once you get it just how you like then you know exactly where to make the change. 

### Live Editing
On top of that you can actually make those changes right in the dev tools them self. By simply clicking on the file name and it will take you to the exact line of the Sass file in the sources tab. If you right click and "Save As" to the same location on as the original file, that is basically save over the original file with itself, then Chrome will know where the file lives and you can save locally right there in the dev tools. You command+s twitch (or I suppose it would be ctrl+s if you are using Linux or Windows) will be all you need. On top of that it will keep a record of all the modifications that you make there and easily let you revert back. Just right click again and select "Local Modifications"

One thing to note here is that you will want to be sure that you are having something (compass in my case) watching your Sass files for changes, otherwise the changes that you make to your Sass files will not be reflected in your CSS until you compile again. I also rely heavily on [LiveReload](https://chrome.google.com/webstore/detail/livereload/jnihajbhpnppcggbcgedagnkighmdlei) so that I don't have to refresh the page after every edit. 

### Minor Issues
Sass debug info is not without its issues. These issues are relatively minor though and getting smaller by the day as the Chrome dev tools team is constantly improving things. First, as we noted above, the debug info includes the absolute path to your Sass files. If you are working on a team, this path is likely going to be different for each member. This means that the dev tools will be looking for a files that doesn't exist until you recompile to get the correct path. It can also present an issue with merge conflicts if you aren't careful. Another issue is that you can only edit files that are directly putting styles to the page. This means that if you have mixins or variables defined you won't be able to get to them in the dev tools. Lastly, the nonstandard media queries that are used in your CSS are really a hack. It does work, but it feels slightly dirty. They also require special tools to read them. Chrome dev tools work great for this, of course, and if you are using Firefox then you can checkout [FireSass](https://addons.mozilla.org/en-US/firefox/addon/firesass-for-firebug/). 

## The Future - (Sourcemaps)
Now that you've gotten this far, everything I just told you will soon be thrown out for something better, sourcemaps. Sourcemaps work by creating a separate json map file that tells the dev tools which lines in your CSS are generated by with lines in your Sass. Then your CSS has a single comment at the bottom pointing to this json file. This means that your CSS remains free of crazy nonstandard media queries and you can easily share files without worrying about merge conflicts. 

Sourcemap support is available today, but with a few caveats. First, they don't work with compass yet. Also they require that you install the bleeding edge version of Sass. This means that you'll need to run your Sass compilation from the command line so GUI tools like [Codekit](http://incident57.com/codekit/) won't work for you.

I am not using sourcemaps in my projects yet, but am looking forward to using them once the last of the wrinkles are ironed out. I'll quickly walk you through how to get them going so that you can give them a go your self. First, we will need to get Sass 3.3 (currently a pre-release version). You can do this by running `sudo gem install sass --pre` in your terminal. To check to make sure that everything worked, run `sass --version`. Make sure that it says Sass 3.3. Next, you'll need to enable experimental features like we did above by going to about:flags and enable Sass support in the settings and then, while you are still in the settings, find and check the "enable sourcemaps support" box under the general tab.

Now head back to the terminal to compile your Sass. Run `sass --watch --sourcemap style.sass:style.css`, replacing your file names accordingly. Now you will notice that your CSS file looks much better than before when we used Sass debug info. There are no wacky media queries, just regular looking CSS with that small comment at the bottom pointing to another file that Sass generated - in our case, style.css.map. This is our sourcemap and it consists of json with mapping between our Sass and CSS files that Chrome understands. The file paths are relative so the map file won't cause merge conflicts.

## This Post Sits on Quicksand
The very nature of this post means that a lot it will soon be out of date. If you find an error feel free to send me a [pull request](https://github.com/bryanstedman/bryanstedman.com/blob/gh-pages/_posts/2013-06-08-working-with-sass-in-the-chrome-dev-tools.md) as this blog is hosted on [Github](https://github.com/bryanstedman/bryanstedman.com). With that in mind, small changes - typo and the like, can go inline, but I'll move any edits that are a result of updates to the underlying technologies to an "Edits" section at the top so they are easy to find.