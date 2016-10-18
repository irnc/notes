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
