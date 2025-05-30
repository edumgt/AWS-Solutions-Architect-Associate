https://aws.amazon.com/ecs/
https://aws.amazon.com/containers/services/

# Container
A container is a standardized unit that packages your code and its dependencies. This package is designed to run reliably on any platform, because the container creates its own independent environment.
There are no time-out limits when running. This is useful for applications that run longer than 15 minutes or that need to initiate instantly when called.

# Amazon Elastic Container Service (Amazon ECS)

![ecs](/img/ecsconstruct3.png)

Amazon ECS is an end-to-end container orchestration service that helps you spin up new containers. With Amazon ECS, your containers are defined in a task definition that you use to run an individual task or a task within a service. 

- Serveless with AWS Fargate
- Managed with EC2 Instances cluster by intalling a ECS Container Agent

To prepare your application to run on Amazon ECS, you create a task definition. The task definition is a text file, in JSON format, that describes one or more containers and the resources that you need to run a container, such as CPU, memory, ports, images, storage, and networking information.