# Getting Started

- setup Flow
- `flow init`
- setup Babel
- add babel preset to strip flow types, so code could be evaluated by Node.js

# First type check

Add `// @flow` as a first line to your module. This will tell Flow to type
check it using inferred types only. Thus without further code annotations you
would reap benefits of a types checking.

# Annotating code

- just add Node.js core classes to code, e.g. `Buffer`
  - `function readRequestMessageHeader(data: Buffer) {}`
- this will type check function calls on `buf` instance
  - e.g. it would warn about missing `offset` parameter in `data.readUInt8()`
    function call (Note: `offset` isn't optional, so it should be explicitly
    specified in a call as `data.readUInt8(0)`, not relying on casting of
    `undefined` to `0`).
