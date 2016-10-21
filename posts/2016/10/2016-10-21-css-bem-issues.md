## _drop BEM for a much nicer alternative_

- which still achieves the same effect
  - Twitter Bootstrap is proposed as an alternative
  - instead of `.navmenu--active`, for example, we do `.navmenu.active`

Incentives:
- make full use of CSS' expressiveness and HTML's natural structure
- it makes for much much shorter `class=""` properties
  - which means it's also easier to understand what's going on
  - and this one doesn't really matter most of the time, but it makes for a smaller bandwidth usage

Pain points:
- BEM currently creates a lot of extra CSS selectors in our HTML and the selectors are long.
  - readability does not benefit and we have a big issue with double css declarations.


## you have a button, do you call it “.mainbutton” and in css target it, of call it “.button .red .center"

- opposites:
  - you give everything a unique class,
  - you give things classes such as `center` and `mobile-only`

##  twitter/foundation way

- namespace the component
- allow modifiers on a class and build your component that way.
