https://aws.amazon.com/ecs/
https://aws.amazon.com/containers/services/

# Container
A container is a standardized unit that packages your code and its dependencies. This package is designed to run reliably on any platform, because the container creates its own independent environment.
There are no time-out limits when running. This is useful for applications that run longer than 15 minutes or that need to initiate instantly when called.

Use case:
- Applications that are compute intensive run better in a container environment. If you have a small application that runs under in 15 minutes but is compute intensive, consider using a container. 
- Large monoliths that have many parts are very suitable applications to consider moving to containers. 
- microservices, using containers to isolate processes.
- With containers, you can package entire applications and move them to the cloud without the need to make any code changes. 
- Dont use When applications need persistent data storage
- Dont use When applications have complex networking, routing, or security requiremen

# Amazon Elastic Container Service (Amazon ECS)

![ecs](/img/ecsconstruct3.png)

Amazon ECS is an end-to-end container orchestration service that helps you spin up new containers. With Amazon ECS, your containers are defined in a task definition that you use to run an individual task or a task within a service. 

- Serveless with AWS Fargate
- Managed with EC2 Instances cluster by intalling a ECS Container Agent

To prepare your application to run on Amazon ECS, you create a task definition. The task definition is a text file, in JSON format, that describes one or more containers and the resources that you need to run a container, such as CPU, memory, ports, images, storage, and networking information.