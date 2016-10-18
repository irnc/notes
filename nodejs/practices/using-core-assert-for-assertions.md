- https://nodejs.org/api/assert.html

## Pros

- minimalistic locked API
  - it is only 14 functions
  - no other functions would be added to it

## Cons

- no support for higher-level assertions

## Practical Hints

- Write assert messages so they are read as _assert that `message`_.
  - _assert that array keys are placed at the end_
  - _assert that object was not modified_

## Alternatives

- `chai`
