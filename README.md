#Introduction
Early days, this is my first themeing experiment for Drupal 8 and is
the theme for running-on-drupal8.com on version Beta 7.

The theme shares the same css as my blog personal site [chris-david-hall.info](http://chris-david-hall.inf) which runs on ExpressionEngine, which is a testement to the greater ease of de-drupalification
of Drupal 8. 

This is just for interest, this would not be useful as base theme or for any
other custom development.

This theme relies on [Sinatra](https://github.com/chris-hall-hu/sinatra)(another learning experiment) as a parent theme.
Sinatra is eventually going to override many of the core Twig templates to provide (Twig Blocks)[http://twig.sensiolabs.org/doc/tags/block.html] that may then
be extended in child themes.

#Bootstrap based
Based on Bootstrap 3 at the moment but the css is a little stripped down and 
the js has been replaced with 
[tagwa/bootstrap-without-jquery](https://github.com/tagawa/bootstrap-without-jquery)

#Going forward
Still a lot more to strip out, and bugs to investigate (which may or may not be
be Drupally bugs at the moment).

Also it already had lots of things wrong with it, on the original theme.  

This may develop into something more interesting depending on which directions
my experiments go in. 

#Heads up
Things and refinements as I notice them that could be useful to others starting a theme from scratch.

## General
When trying out a new theme install and set as default in one step can be unpredictable, installing and then setting 
the theme as default in two steps can often be a lot more informatative if there is a problem with the theme.

## Some useful css for stripped down themes
You can remove css style sheets added by modules etc. for example in the theme info.yml
```
stylesheets-remove:
  - views.module.css
  - system.module.css
  - system.theme.css
```
A few css rules are still really useful to make the admin toolbar work, alignment styles from the CCK WYSIWYG etc. these styles are obtained from
the parent theme [Sinatra](https://github.com/chris-hall-hu/sinatra)(another learning experiment).

## Themes can have config also
I added the yaml config for my repsonsive image styles to this theme (really just as a reminder for when I am doing real themeing),
[see this article](http:d//running-on-drupal8.co.uk/article/drupal8-responsive-breakpoints). Note however that setting theme as default 
will fail if you don't have required module dependencies for the config (as of now the error message is not very specific).

## Admin menu width is defined in rems
If you want the admin menu to work nice with your new theme then you need to take into account that it's width is measured in rems and is therefore relative to the html font-size (the font-size specified when you inspect your html tag). 

It assumes by default that this will be 16px, but if your are using bootstrap or a theme that uses the trick of setting the font-size on the html element to be 62.5% (because 10px is lot easier to do font-scaling calculations with) then horizontal admin menu will be too thin (doh). 

You either need to set the html font-size to 100% (if that doesn't break anything else) or do some CSS with the width of the #toolbar-item-administration-tray to fix.

## Admin menu needs classes from Classy theme
Starting from a more barebones theme I noticed that the Admin menu is styled wrong, it needs some extra stuff added from Classy (menu.html.twig). 

You can fix this in a theme that is not a subtheme of Classy by copying the Classy menu.html.twig template into your theme as menu--admin.html.twig.




