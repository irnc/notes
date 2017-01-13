# What developer should know about `passport`

```coffee
passport = require 'passport'
passport.use someStrategy
```

```coffee
someStrategy = new LocalStrategy options, verify
```

```coffee
verify = (email, password, done) ->
  success = (user) -> done(null, user || false)
  failure = (err) -> done(err)

  loginService.login({ email, password }).then success, failure
```

```coffee
app.use passport.initialize()
app.use createAuthenticationMiddleware(passport)
app.use routes
```

```coffee
createAuthenticationMiddleware = (passport) -> (req, res, next) ->
  # Skip if no authentication token.
  if !req.headers.authorization
    return next()

  options =
    session: false

  onVerified = (err, user, challenge, status) ->
    if err
      log.error err, 'failed to authenticate user using jwt-bearer strategy'

    if user == false
      log.error { challenge, status }, 'failed to verify JWT token'

    if user
      return req.login(user, options, next)

    # Ignore authentication and verification errors.
    next()

  passport.authenticate('jwt-bearer', options, onVerified)(req, res, next)
```

## code

https://github.com/jaredhanson/passport

- `req.login` and `req.logout`
  - https://github.com/jaredhanson/passport/blob/master/lib/http/request.js
- `passport.authenticate` and strategy augmentation, e.g. `.fail` and `.success`
  - https://github.com/jaredhanson/passport/blob/master/lib/middleware/authenticate.js
- `Strategy`
  - https://github.com/jaredhanson/passport-strategy
- HTTP Bearer strategy
  - https://github.com/jaredhanson/passport-http-bearer/blob/master/lib/strategy.js
  - https://github.com/FloeDesignTechnologies/passport-http-jwt-bearer/blob/master/lib/strategy.js
