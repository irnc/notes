## `credentials.get()`

_NotAuthorizedException: Token is not from a supported provider of this identity pool._

- Happens when Facebook identity is given, while identity poll is not connected
  to Facebook application.
- Solution: specify Facebook App ID while editing federated identity pool at
  Cognito.
