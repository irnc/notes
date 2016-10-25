## Plan

- Terraform configuration for API Gateway
- Manual Cognito setup
  - no Terraform support https://github.com/hashicorp/terraform/issues/8309
- Manually adding Cognito Autorizer to API Gateway
- aws-sdk + Facebook SDK
- https://github.com/aws/amazon-cognito-identity-js
- deployment and API generation
  - http://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-generate-sdk.html

## SDK Generation

- http://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-generate-sdk.html
- http://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-generate-sdk-javascript.html
- https://github.com/kndt84/aws-api-gateway-client
- https://github.com/guzmonne/meraki-quotes/blob/master/src/aws-sdk.import.js

TK Integrate generated SDK using webpack and `script-loader`, just `npm i` it.

## Making requests

- enable CORS
  - http://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-cors.html
  - https://github.com/carrot/terraform-api-gateway-cors-module

## Frustrating Cognito User Pool Authorizer

- 401 Unauthorized and `x-amzn-ErrorType: UnauthorizedException`
  - when Authorizer is set to Cognito User Pool Authorizer
- Standard _Cognito User Pool Authorizer_ is usable only for user pools, i.e.
  there is no way to authenticate users using federated identity.

No way gluing API Gateway with Cognito Federated Identities without Lambda.

http://docs.aws.amazon.com/apigateway/latest/developerguide/use-custom-authorizer.html

## 415 Unsupported Media Type

- API Gateway method could respond with 415 status code.
- In that case, check out `Content-Type` in request headers, in my case it was
  `Content-Type: text/plain;charset=UTF-8`.

Debug session:
- `dispatchRequest` is called with `config.headers['Content-Type']` set to
  `application/json`.
- inside `xhrAdapter` there is a `// Remove Content-Type if data is undefined`
- OK, I need to set data... but data is already passed... actually not
- `apigClient` methods has `(params, body)` signature

## CORS

- Integration Response should set allow-origin header
- Method Response should proxy allow-origin header
- TK update https://github.com/irnc/terraform-api-gateway-cors-module

## `response.data` could be string

- even when `response.headers['content-type'] === 'application/json'`
- this happens when JSON couldn't be parsed, e.g. is contains `#` left from
  comments.
- Terraform's template doesn't have notion of a comment, while Velocity
  uses `##` as a comment mark.
