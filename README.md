TWITTER BOOTSTRAP - SANDBOXED
=============================

Bootstrap is Twitter's toolkit for kickstarting CSS for websites, apps, and more. It includes base CSS styles for typography, forms, buttons, tables, grids, navigation, alerts, and more.

The main repo is here: http://github.com/twitter/bootstrap

And the example page is here: http://twitter.github.com/bootstrap


This Sandbox Version
--------------------

Sometimes you're stuck using someone else's css on a page, but you do have control over your div -- if only you could bring in twitter-bootstrap to style your widget, and not break everything else along with it.  You can with this sandboxed version!

This fork allows you to break free of the css world you're in now, and create a little sandbox on your page where you can use twitter bootstrap without clobbering all the other styles AND without having the other styles clobber your little twitter-bootstrap world.


The Big Assumption
------------------

To sandbox, I've used the trick of overspecifying every style.  I've chosen to prepend every style with two id tokens (#t #b).  This will keep the sandboxed twitter-bootstrap from affecting the outer css world ONLY if that world has specificity less than or equal to the sandboxed styles.  To say it another way, you will be safe if the pre-existing css on the page never uses more than 1 id token in its css declarations.  You're probably still safe if it uses 2 id tokens in a single css declaration, except in rare cases.  If you have any stylings using 3, then this might not work so well.

Usage
-----
All of the twitter-bootstrap styles have been sandboxed by prepending them with #t #b, so to take advantage, you'll need to wrap your widget in html like this:

```html
<div id="t">
  <div id="b">
    ha ha rest-of-this-html-page, I can do twitter bootstrap stuff here and you can't
  </div>
</div>
```

And of course you'll need to inlcude a link to the css, you'll probably wanna add it to the end of your css link list, so it retains maximum specificity.

``` html
<link rel="stylesheet/less" type="text/css" href="bootstrap-sandbox.css" />
```

For any custom styles you want inside the sandbox, you'll find that you often need to prepend them with #t #b to make them specific enough to catch -- it depends on the style.  It's probably good habit to just do this for everything so you don't waste time figuring it all out.


Relevant Changes from Bootstrap
-------------------------------
1) rewrite all root level specifications (html & body) to use "#t #b"

2) prepend all other specifications with "#t #b"

3) remove the scrollbar in reset.less on #t #b

