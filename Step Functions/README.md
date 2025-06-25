
# AWS Step Functions

AWS Step Functions is a fully managed service that you can use to coordinate the components of distributed applications and microservices using visual workflows
Step Functions is a reliable way to coordinate components and step through the functions of your application.
Step Functions automatically invokes and tracks each step and retries when errors occur.
Serverless technologies eliminate infrastructure management tasks like capacity provisioning and patching, so you can focus on writing code that serves your customers.
Flexible scaling

Orchestration centrally manages a workflow by breaking it into multiple steps, adding flow logic, and tracking the inputs and outputs between the steps.
As your applications run, Step Functions maintains the application state,  Individual states can make decisions based on their input, perform actions, and pass output to other states.

With step functions, you can define and manage the workflow of your application independently from its business logic. Making changes to one does not affect the other. 
AWS Step Functions keeps your application logic strictly separated from the implementation of your application. You can add, move, swap, and reorder steps without having to make changes to your business logic

Type of states:
- Pass state: dont perform a work, inject some fixed data.
- Task: perform a work by using an activity, API Actions or an AWS Lambda function
- Choice: adds branching logic
- Wait: delays the state machine
- Succeed: stops an activity successfully
- Fail: stops the activity of the state machine and marks it as a failure, unless it is caught by a Catch block.
- Parallel: can be used to create parallel branches of activity
- Map: can be used to run a set of steps for each element of an input array.
- Intrinsic functions for basic operations without Task states. This can be used to help Payload Builders process the data going to and from Task Resources:
    - States.Format:
    - States.StringToJson:
    - States.JsonToString:
    - States.Array:

The Step Functions console provides a graphical representation of that state machine to help visualize your application logic.
The Amazon States Language is a JSON-based, structured language used to define your state machine

Step Functions, when invoked, receives a JSON text as input and passes that input to the first state in the workflow. Individual states receive JSON as input and usually pass JSON as output to the next state.

### Features
- Auto-Scaling
- High availability: AWS Step Functions has built-in fault tolerance and maintains service capacity across multiple Availability Zones in each region to protect applications against individual machine or data center failures
- Pay per use: you pay for each transition from one state to the next. you do not pay for idle time
- Security an compliance: IAM, Step function is compliant with SOC and a HIPAA eligible service

### Orchestration features
- AWS Service Integration
- Error handling: AWS Step Functions automatically handles errors and exceptions with built-in try/catch and retry
- Logs history: AWS Step Functions delivers real-time diagnostics and dashboards, integrates with Amazon CloudWatch and AWS CloudTrail, and logs every execution
- Visual monitoring
- High volume orchestration: supports event rates greater than 100,000 per second