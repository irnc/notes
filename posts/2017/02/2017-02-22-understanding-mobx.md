# What is MobX?

Short egghead course: https://egghead.io/courses/manage-complex-state-in-react-apps-with-mobx

[_MobX is a general purpose FRP library [...]._][1]

[1]: https://egghead.io/lessons/javascript-mobx-and-react-intro-syncing-the-ui-with-the-app-state-using-observable-and-observer?course=manage-complex-state-in-react-apps-with-mobx

# What is an FRP library?

TK

# MobX for a developer used to redux

- there is no reducers, components change the state directly
  - using implicit or explicit _actions_
  - _Actions modify a state [...]_ https://egghead.io/lessons/react-mobx-fundamentals-changing-and-guarding-state-using-actions
- _observer_ is a case of _reaction_, it triggers `render` on change to observable
  - _transaction_ could group changes before running a reaction
  - _explicit action_ applies transaction automatically
- in MobX, state is objects data, actions are objects behavior
  - MobX leans to object-oriented principles, while redux is to functional
