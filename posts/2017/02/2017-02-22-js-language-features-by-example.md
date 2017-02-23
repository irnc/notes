# Next

https://github.com/tc39/proposals

## Decorators

- on stage 2 as of February 2017
- MobX
  - https://github.com/mobxjs/mobx
  - https://egghead.io/courses/manage-complex-state-in-react-apps-with-mobx

# ECMAScript 2017 (draft)

https://github.com/tc39/proposals/blob/master/finished-proposals.md

# ECMAScript 2016

https://www.ecma-international.org/ecma-262/7.0/

- the exponentiation operator (\**),
- Array.prototype.includes (not to be confused with ClassList.contains).

# ECMAScript 2015

https://github.com/lukehoban/es6features

## Template Literals

- https://github.com/styled-components/styled-components
- https://github.com/cezary/sql-query-tag

## Classes

- React.Component

```js
class Temperature {
  unit = 'C';
  temperatureCelsius = 25;

  get temperatureKelvin() {
    return this.temperatureCelsius * (9/5) + 32
  }

  get temperatureFahrenheit() {
    return this.temperatureCelsius + 273.15
  }
}
```
