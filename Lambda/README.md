https://aws.amazon.com/lambda/serverless-architectures-learn-more/
https://aws.amazon.com/blogs/compute/best-practices-for-organizing-larger-serverless-applications/

# AWS Lambda

Lambda runs your code on a high availability compute infrastructure and requires no administration from the user. 
You upload your source code in one of the languages that Lambda supports, and Lambda takes care of everything required to run and scale your code with high availability. 

You can invoke your function directly by using the Lambda API, or you can configure an AWS service or resource to invoke your function in response to an event.

Triggers describe when a Lambda function should run. A trigger integrates your Lambda function with other AWS services and event source mappings.

An event is a JSON-formatted document that contains data for a Lambda function to process. The runtime converts the event to an object and passes it to your function code. 

You deploy your Lambda function code using a deployment package. Lambda supports two types of deployment packages:
- A .zip file archive – This contains your function code and its dependencies. Lambda provides the operating system and runtime for your function.
- A container image – This is compatible with the Open Container Initiative (OCI) specification. You add your function code and dependencies to the image. You must also include the operating system and a Lambda runtime.

Pricing: You are charged for the number of times that your code is invoked (requests) and for the time that your code runs

This service is not for long-running proceses like deep learning or batch jobs. If an application needs to run longer than 15 minutes, it's no longer cost effective to use Lambda. Instead, consider other solutions.

Lambda runs your function in multiple Availability Zones to ensure that it is available to process events in case of a service interruption in a single zone. 

Use case: 
- small, simple, or modular application
- applications less compute intensive
- Serverless is a very appropriate fit when you need one action to invoke other workflows within AWS.
- applications that don't run longer than 15 minutes.