```js
describe('service', () => {
  const scopes = {};

  beforeEach(() => {
    scopes.foo = nock(config.FOO_ENDPOINT);
    scopes.bar = nock(config.BAR_ENDPOINT);
  });

  afterEach(() => {
    R.values(scopes).forEach(scope => {
      scope.done();
    });
  });

  it('should create book', () => {
    scopes.foo.post('/books', { test: 'true' }).reply(201, { test: 'true' });

    // NOTE that we create HTTP interceptor using nock, but call proxy API.
    return service.createBook()
      .then(res => {
        assert.deepEqual(res, { status: 'created' });
      });
  });
});
```

- this isn't integration test, we don't integrate communicating services
- this is a unit test, where unit is an HTTP endpoint
