https://aws.amazon.com/lambda/serverless-architectures-learn-more/
https://aws.amazon.com/blogs/compute/best-practices-for-organizing-larger-serverless-applications/
https://d1.awsstatic.com/whitepapers/AWS_Serverless_Multi-Tier_Architectures.pdf

# AWS Lambda
AWS Lambda is an event-driven, serverless compute service that lets you run code without provisioning or managing servers.

Lambda functions are stateless, with no affinity to the underlying infrastructure. Lambda can rapidly launch as many copies of the function as needed to scale to the rate of incoming events.

Lambda runs your code on a high availability compute infrastructure and requires no administration from the user. 
You upload your source code in one of the languages that Lambda supports, and Lambda takes care of everything required to run and scale your code with high availability. 

In event-driven architectures, events are the primary mechanism for sharing information across services.

You can invoke your function directly by using the Lambda API, or you can configure an AWS service or resource to invoke your function in response to an event.

Triggers describe when a Lambda function should run. A trigger integrates your Lambda function with other AWS services and event source mappings.

This service is not for long-running proceses like deep learning or batch jobs. If an application needs to run longer than 15 minutes, it's no longer cost effective to use Lambda. Instead, consider other solutions.

Lambda runs your function in multiple Availability Zones to ensure that it is available to process events in case of a service interruption in a single zone. 

### Performance and costs
These settings are important in defining how each function performs: memory, timeout, and concurrency. As you monitor your functions, you must adjust the settings to optimize costs and ensure the desired customer experience with your application.
- Any increase in memory size triggers an equivalent increase in CPU available to your function. To find the right memory configuration for your functions, use the AWS Lambda Power Tuning tool.
- A single invocation of a Lambda function cannot run longer than 900 seconds (which is 15 minutes). Avoiding lengthy timeouts for functions can prevent you from being billed while a function is simply waiting to time out.
- Lambda functions also have a Regional concurrency limit (1000) and a reservation system that can be used to set aside runtime for specific instances. No charge is incurred for configuring reserved concurrency for a function. 
- Provisioned concurrency is an option used when you need high performance and low latency, because enviroment are prepared to respond immediately to your function's invocations.. You pay for the amount of provisioned concurrency that you configure and for the period of time that you have it configured. 
- CloudWatch includes two built-in metrics that help determine concurrency: ConcurrentExecutions and UnreservedConcurrentExecutions.

Pricing: You are charged based on the number of requests for your functions and the duration. Price also depends on the amount of memory you allocate to your function, not the amount of memory your function uses. The AWS Lambda Free Tier includes 1 million free requests per month and 400,000 GB-seconds of compute time per month.

### Code
The Lambda function handler is the method in your function code that processes events. The handler method takes two objects:
- Event object: parameters provided to your handler function. An event is a JSON-formatted document that contains data for a Lambda function to process. The runtime converts the event to an object and passes it to your function code. 
- Context object (optional): Lambda execution environment.
Writting code best practices:
- Separate the business logic from the handler method.
- Make your functions modular 
- It is particularly important for serverless applications to treat each function as stateless.
- Should include logging statements
- Functions must give Lambda information about the results of their actions.
- You can use environment variables to store sensitive information required by the function.
- AWS Secrets Manager helps you organize and manage important configuration data such as credentials, passwords, and license keys.

You deploy your Lambda function code using a deployment package. Lambda supports two types of deployment packages:
- A .zip file archive – This contains your function code and its dependencies. Lambda provides the operating system and runtime for your function.
- A container image – This is compatible with the Open Container Initiative (OCI) specification. You add your function code and dependencies to the image. You must also include the operating system and a Lambda runtime.

AWS SAM is an open-source framework for building serverless applications. It provides shorthand syntax to express functions, APIs, databases, and event source mappings. It is an extension of CloudFormation and transform the instruction into a CloudFormation template. You can install the AWS SAM CLI locally to help test your serverless applications, validate your AWS SAM templates, and streamline your deployments.

In a serverless deployment, you provide all the components necessary to deploy your function: 
- Code, bundled with any necessary dependencies
- CloudFormation template, which is the blueprint for building the serverless environment

##### AWS Code Deploy
You can also use routing configuration on an alias to send a portion of traffic to a second function version. 

Lambda is integrated with AWS CodeDeploy for automated rollout with traffic shifting. CodeDeploy supports multiple traffic shifting methods:
- Canary 
- Linear
- All-at-once
When the alarms or hooks trigger a rollback, everything in the CloudFormation template being deployed is rolled back. 

### Use case
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

Permissions to invoke the function are controlled using an IAM resource-based policy. An **IAM execution role** defines the permissions that control what the function is allowed to do when interacting with other AWS services. 

Apply the principle of least privilege with IAM Access Analyzer, which reviews your AWS CloudTrail logs over the date range that you specify and generates a policy template with only the permissions that the function used during that time.

### Networking
Enabling your Lambda function to access resources inside your virtual private cloud (VPC) requires additional VPC-specific configuration information, such as VPC subnet IDs and security group IDs.

To establish a private connection between your VPC and Lambda, create an interface VPC endpoint (powered by AWS PrivateLink). Private connection without an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection. 

### Monitoring

- requests, duration per requests and requests with error. The number of times that a process failed because of concurrency limits. ConcurrentExecutions: UnreservedConcurrentExecutions and ProvisionedConcurrentExecutions 
- Your Lambda functions send trace data to X-Ray, and X-Ray processes the data to generate a service map and searchable trace summaries
    ![trace_lambda_cold_start](/img/trace_lambda_cold_start.png)
    ![trace_lambda_billed](/img/trace_lambda_billed.png)

    start enviroment + initialize function = Cold Start

    Thaw enviroment = Warm Start

    ![trace_lambda_billed_warm](/img/trace_lambda_billed_warm.png)

    Billing duration is reduced by using Warm Start. 

- If an order fails, you cannot ignore that order error. You move that error into the dead-letter queue and manually look at the queue and fix the problems. Interact with SQS (Queue) or SNS (topic)
- AWS CloudTrail helps audit your application by recording all the API actions made against the application. These logs can be exported to the analysis tool of your choice for additional analysis. 