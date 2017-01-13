```
project/
└── lib/
    ├── order-array-properties.js
    └── order-array-properties.test.js
```

Instead of separate `tests/` directory:

```
project/
├── lib/
│   └── order-array-properties.js
└── tests/
    └── order-array-properties.test.js
```

## Pros

- locating unit tests becomes easier

## Cons

- `mocha` would require a special pattern. Example `package.json`:

  ```
  {
    "scripts": {
      "test": "mocha 'lib/**/*.test.js'"
    }
  }
  ```

# Use case: testing application endpoints

- express.js application
- HTTP endpoints
- `src/routes.js` module exports routing application
- express middleware exported from `src/controllers/[plural-entity-name].js`
- tests in `tests/endpoints/[controller-name].spec.js`
  - uses `nock` to mock external services
