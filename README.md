# aws-wildrydes

The application architecture uses AWS Lambda, Amazon API Gateway, Amazon DynamoDB, Amazon Cognito, and AWS Amplify Console.

## AWS Amplify- For Hosting statsic website

Amplify provides continuous deployment and hosting of the static web resources including HTML, CSS, JavaScript, and image files which are loaded in the user's browser.

## AWS Cognito- For Authentication/Authorization

Amazon Cognito user pool to manage users' accounts. It will enable customers to register as a new user, verify their email address, and sign into the site. After users submit their registration, Amazon Cognito will send a confirmation email with a verification code to the address they provided. To confirm their account, users will return to your site and enter their email address and the verification code they received.After users have a confirmed account, they will be able to sign in. When users sign in, they enter their username (or email) and password. A JavaScript function then communicates with Amazon Cognito, authenticates using the Secure Remote Password protocol (SRP), and receives back a set of JSON Web Tokens (JWT). The JWTs contain claims about the identity of the user and will be used to authenticate against the RESTful API you build with Amazon API Gateway.

## AWS Lambda and AWS DynamoDB - For serverless service backend

AWS Lambda and Amazon DynamoDB to build a backend process for handling requests for this web application. The browser application(front-end ) allows users to request that a unicorn be sent to a location of their choice. In order to fulfill those requests, the JavaScript running in the browser will need to invoke a service running in the cloud. So, a Lambda function that will be invoked each time a user requests a unicorn. The function will select a unicorn from the fleet, record the request in a DynamoDB table and then respond to the front-end application with details about the unicorn being dispatched.

## AWS API Gateway- To Invoke Lambda function from the browser using Amazon API Gateway

We use Amazon API Gateway to expose the Lambda function as a RESTful API. This API will be accessible on the public Internet. It will be secured using the Amazon Cognito user pool. Using this configuration we will then turn our statically hosted website into a dynamic web application by adding client-side JavaScript that makes AJAX calls to the exposed APIs.
