- terminal-plus package forking
  - see /posts/2016/11/2016-11-04-atom-terminal.md
  - https://github.com/platformio/platformio-atom-ide-terminal
  - https://github.com/fusion809/terminal-fusion
  - https://github.com/Fred-Barclay/Termination
    - https://github.com/jeremyramin/terminal-plus/issues/451
- pty.js forking
  - https://github.com/chjj/pty.js
  - https://github.com/jeremyramin/pty.js
  - https://github.com/platformio/pty.js

# terminal-plus package forking

Issues debating use of outdated nan in pty.js package:

- https://github.com/tensor5/arch-atom/issues/12
- https://github.com/platformio/platformio-atom-ide-terminal/pull/39
- https://github.com/platformio/platformio-atom-ide-terminal/issues/79

> @fusion809 [why do you need][] "yet another fork"?
>
> _Not much of a reason why, I just created it because I wanted to release a
> version of the package with the `linux` theme ASAP. Oh and that reminds me
> I'm gonna go offer a solution to one of your issues on this repo._

PlatformIO position outlined by Ivan Kravets:

> I propose to support the one fork and merge it to original @jeremyramin's when he will be back

[why do you need]: https://github.com/platformio/platformio-atom-ide-terminal/pull/39#issuecomment-225935706

`fusion` fork and that discussion happened between June 6 and 14, 2016. While
there was no commits to `terminal-plus` from Dec 29, 2015 (other than three
commits in September - October 2016).

`terminal-plus` seemed to be [abandoned][] at April 2016.

[abandoned]: https://github.com/jeremyramin/terminal-plus/pull/235

[Changes][] done by Brenton Horne at `terminal-fusion` could be seen at GitHub:

- name added to copyright holders
- symbols changed from `platformio-ide-terminal` to `terminal-fusion`
- README updated to use UK English instead of US variant
- `linux` theme added with dark background?

Was there a way to add theme without a fork? There is how [`dracula`][] theme
was added at Nov 21, 2015.

[`dracula`]: https://github.com/jeremyramin/terminal-plus/pull/106

[Changes]: https://github.com/fusion809/terminal-fusion/compare/5fd8aeed96ba47820918a15fe996e76a824ac8aa...master

# Jeremy Ebneyamin

- https://github.com/jeremyramin
- https://www.linkedin.com/in/ebneyaminj/
- https://www.youtube.com/channel/UCbHM0nPILP01M1Sd-zGmgqA
- university
  - https://github.com/Lupo-CalPoly/cpe-315-fall-2016-lab-1-jeremyramin
  - http://www.catalog.calpoly.edu/coursesaz/cpe/
  - http://users.csc.calpoly.edu/~clupo/teaching/315/winter17/
    - TK they use https://piazza.com/ for Q&A
  - TK another persons assignment, https://github.com/joelbraun/PolyAppDevAPI

## `terminal-plus`

- it all started August 21, 2015
  - https://github.com/jeremyramin/terminal-plus/commit/e9dfeb4ceb8aad183da5d3f64394f275ab17cdee

# Atom package discoverability

- https://atom.io/packages/search?q=terminal
  - 1st terminal-plus, 271,665 downloads
  - 3rd tokamak-terminal, 7,894
  - 4th terminal-fusion, 9,090
  - 7th platformio-ide-terminal, 207,712
- http://atom-packages.directory/category/tools-terminal/
  - better for some tasks, as provides curated catalog
  - open sourced at https://github.com/bastilian/atom-packages.directory
  - http://atom-packages.directory/package/terminal-fusion/
    - _Terminal Fusion  by Jeremy Ebneyamin_ isn't right, but I guess it is
      metadata issue
