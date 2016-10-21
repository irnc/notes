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
