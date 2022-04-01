# How it was created

I followed a tutorial on AWS official website to build this project. Feel free to take a look: <a href="https://aws.amazon.com/getting-started/hands-on/build-serverless-web-app-lambda-apigateway-s3-dynamodb-cognito/" target="_blank"  > Link </a>

# About it

Unicorns are faster, safer, and more reliable. In recent times, their numbers have grown significantly, reaching a scale that makes it finally possible to harness them for mass transportation at an affordable cost. So this web app will allow an authenticated User to call a Unicorn for a ride. Cool, isn't it??

# aws-wildrydes

The application architecture uses AWS Lambda, Amazon API Gateway, Amazon DynamoDB, Amazon Cognito, and AWS Amplify services from Amazon Web Services.

## AWS Amplify- For Hosting this web application

AWS Amplify provides continuous deployment and hosting of this website with resources including HTML, CSS, JavaScript, and image files which are loaded in the user's browser.

## AWS Cognito- For Authentication/Authorization

Amazon Cognito user pool to manage users' accounts. It will enable customers to register as a new user, verify their email address, and sign into this web application. After users submit their registration, Amazon Cognito will send a confirmation email with a verification code to the address they provided. To confirm their account, users will return to this web application and enter their email address and the verification code they received. After users have a confirmed account, they will be able to sign in. When users sign in, they enter their username (or email) and password.Under the hood, A JavaScript function then communicates with Amazon Cognito, authenticates using the Secure Remote Password protocol (SRP), and receives back a set of JSON Web Tokens (JWT). The JWTs contain claims about the identity of the user and will be used to authenticate against the RESTful API we have built with Amazon API Gateway.

## AWS Lambda and AWS DynamoDB - For Serverless Back-end

AWS Lambda and Amazon DynamoDB build a backend process for handling requests for this web application. The browser application(front-end ) allows users to request that a unicorn be sent to a location of their choice. In order to fulfill those requests, the JavaScript running in the browser will need to invoke a service running in the cloud. So, a Lambda function that will be invoked each time a user requests a unicorn. The function will select a unicorn from the fleet, record the request in a DynamoDB table and then respond to the front-end application with details about the unicorn being dispatched.

## AWS API Gateway- To Invoke Lambda function from the browser using Amazon API Gateway

Amazon API Gateway is used to expose the Lambda function as a RESTful API. This API will be accessible on the public Internet. It will be secured using the Amazon Cognito user pool. Using this configuration we will then turn our statically hosted website into a dynamic web application by adding client-side JavaScript that makes AJAX calls to the exposed APIs.
