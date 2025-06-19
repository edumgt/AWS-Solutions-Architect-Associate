https://aws.amazon.com/lambda/serverless-architectures-learn-more/
https://aws.amazon.com/blogs/compute/best-practices-for-organizing-larger-serverless-applications/

# AWS Lambda
AWS Lambda is an event-driven, serverless compute service that lets you run code without provisioning or managing servers.

Lambda functions are stateless, with no affinity to the underlying infrastructure. Lambda can rapidly launch as many copies of the function as needed to scale to the rate of incoming events.

Lambda runs your code on a high availability compute infrastructure and requires no administration from the user. 
You upload your source code in one of the languages that Lambda supports, and Lambda takes care of everything required to run and scale your code with high availability. 

In event-driven architectures, events are the primary mechanism for sharing information across services.

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

### Invocation models for running Lambda functions
It's important to understand how each invocation model initializes functions and handles errors and retries. 

- Synchronous invocation: Lambda runs the function and waits for a response. There are no built-in retries. You must manage your retry strategy within your application code. Invoke Services: API Gateway, Cognito, Alexa, Lex, CloudFront.
- Asynchronous invocation: Events are queued and the requestor doesn't wait for the function to complete. A destination can send records of asynchronous invocations to other services. There are Built in – retries twice. Invoke Services: SNS, S3 and EventBridge.
- Polling invocation: AWS will manage the poller on your behalf and perform synchronous invocations of your function. Invoke services: Kinesis, SQS and DynamoDB Streams.

Provisioned concurrency is a Lambda feature that prepares concurrent execution environments before invocations and ensures the lowest possible latency. Useful to avoid the case when the environment is not already initialized, the start-up time of the environment adds to latency. 

Best practice: Write functions to take advantage of warm starts
1. Store and reference dependencies locally.
2. Limit re-initialization of variables.
3. Add code to check for and reuse existing connections.
4. Use tmp space as transient cache.
5. Check that background processes have completed.