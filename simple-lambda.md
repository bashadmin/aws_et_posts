# Creating a Simple AWS Project with Lambda, API Gateway, Node.js, and Postman

## Introduction

Welcome to this tutorial where we'll build a simple AWS project using AWS Lambda, API Gateway, Node.js, and Postman. This project will demonstrate how to create a serverless API that can be tested and used through Postman. Whether you're new to AWS or looking to expand your skills, this guide will walk you through each step.

## Prerequisites

- AWS Account
- Basic understanding of Node.js
- Postman installed on your system
- Familiarity with AWS Management Console

## Step 1: Setting Up AWS Lambda

AWS Lambda allows you to run code without provisioning or managing servers. We'll start by creating a simple Lambda function in Node.js.

1. **Log in** to your AWS Management Console.
2. Navigate to **Lambda** and click on **Create function**.
3. Choose **Author from scratch**.
4. Enter a **Function name**, like `MyLambdaFunction`.
5. Select **Node.js** as the runtime.
6. Click on **Create function**.

## Step 2: Writing Lambda Function Code

1. In the Lambda function dashboard, navigate to the **Function code** section.
2. Replace the existing code in `index.js` with the following Node.js code:

   ```javascript
   exports.handler = async (event) => {
       let responseMessage = 'Hello from Lambda!';

       if (event.queryStringParameters && event.queryStringParameters.name) {
           responseMessage = 'Hello, ' + event.queryStringParameters.name + '!';
       }

       const response = {
           statusCode: 200,
           body: JSON.stringify({ message: responseMessage }),
       };

       return response;
   };
   ```

3. Click **Save**.

This code will make the Lambda function return a personalized greeting message if a name is provided.

## Step 3: Creating an API Gateway

AWS API Gateway will help us expose the Lambda function as a REST API.

1. Go to the **API Gateway** service in the AWS console.
2. Click on **Create API**.
3. Select **HTTP API** and click on **Build**.
4. Under **Configure routes**, add a route (e.g., `/greet` with the `GET` method).
5. For the **Integration target**, select your previously created Lambda function.
6. Click on **Create**.

## Step 4: Deploying the API

1. In the API Gateway dashboard, navigate to **Deployments**.
2. Click on **Create**.
3. Select a **Stage** (e.g., prod) and click on **Deploy**.

Once deployed, you'll receive a URL endpoint for your API.

## Step 5: Testing with Postman

1. Open Postman on your computer.
2. Create a new request and set the method to `GET`.
3. Paste the API endpoint URL you received after deployment.
4. Add a query parameter `name` with a value of your choice (e.g., `name=John`).
5. Click on **Send**.

You should receive a response from your Lambda function.

## Reflection

Congratulations! You've successfully created a serverless API using AWS Lambda and API Gateway, and tested it with Postman. This project serves as a basic foundation for building more complex serverless applications on AWS.

Feel free to modify the Lambda function and experiment with different API Gateway settings to understand their capabilities better. Happy coding!

Remember, AWS offers extensive documentation and a supportive community for further exploration. Don't hesitate to dive deeper into each of these services to master AWS. Please feel free to view some of the resources I suggest to look at below.

## Links
[View Well Architected resources](https://aws.amazon.com/architecture/well-architected/)

[Go try some labs](https://www.wellarchitectedlabs.com/)