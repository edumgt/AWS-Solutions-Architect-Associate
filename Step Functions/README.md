
# AWS Step Functions

AWS Step Functions is a fully managed service that you can use to coordinate the components of distributed applications and microservices using visual workflows
Step Functions is a reliable way to coordinate components and step through the functions of your application.
Step Functions automatically invokes and tracks each step and retries when errors occur.
Serverless technologies eliminate infrastructure management tasks like capacity provisioning and patching, so you can focus on writing code that serves your customers.
Flexible scaling

Orchestration centrally manages a workflow by breaking it into multiple steps, adding flow logic, and tracking the inputs and outputs between the steps.
As your applications run, Step Functions maintains the application state,  Individual states can make decisions based on their input, perform actions, and pass output to other states.

Type of states:
- Pass state: dont perform a work, inject some fixed data.
- Task: perform a work by using an activity, API Actions or an AWS Lambda function
- Choice: adds branching logic
- Wait: delays the state machine
- Succeed: stops an activity successfully
- Fail: stops the activity of the state machine and marks it as a failure, unless it is caught by a Catch block.
- Parallel: can be used to create parallel branches of activity
- Map: can be used to run a set of steps for each element of an input array.
