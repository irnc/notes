_Find the smallest amount of state you need, and derive all the other things._ That was stated for MobX.

https://egghead.io/lessons/javascript-mobx-fundamentals-deriving-computed-values-and-managing-side-effects-with-reactions

The same practice is applied to Redux state.

# Why functions without side effects?

- to allow _system_ to run them at any moment it decides it should run them
  - system could be redux, MobX reactions
