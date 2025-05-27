https://aws.amazon.com/cloudwatch/
https://aws.amazon.com/sns/

# Monitoring
You need a way to collect and analyze data about the operational health and usage of your resources.
Monitoring provides a near real-time pulse on your system and helps answer the following questions:
- How many people are visiting my site day to day?
- How can I track the number of visitors over time?
- How will I know if the website is having performance or availability issues?
- What happens if my Amazon Elastic Compute Cloud (Amazon EC2) instance runs out of capacity?
- Will I be alerted if my website goes down?

Metrics
The AWS resources that host your solutions create various forms of data that you might be interested in collecting. Each individual data point that a resource creates is a metric. Metrics that are collected and analyzed over time become statistics, such as average CPU utilization over time showing a spike.

Use:
- Respond to operational issues proactively before your end users are aware of them.
- Monitoring can improve the performance and reliability of your resources
- You can recognize security threats and events.
- Monitoring helps you make data-driven decisions for your business. monitoring helps you to find which users use the new feature.
- Through monitoring, you can create more cost-effective solutions.

# CloudWatch

CloudWatch is a monitoring and observability service that collects and analyzes your resource data in a centralized place and provides actionable insights into your applications

Use:
- Detect **anomalous behavior** in your environments.
- Set **alarms** to alert you when something is not right.
- Visualize **logs and metrics** with the AWS Management Console.
- Take automated actions like **scaling**.
- **Troubleshoot** issues.
- Discover insights to keep your applications **healthy**.

![How_CW_works2](/img/How_CW_works2.png)

Types:
- Basic monitoring (free): 1 data point per metric per 5-minute interval for default metrics
- Detailed monitoring (fee): metrics every minute for default metrics
- Custom metrics (fee): Your own application metrics. You can send 1 data point per second per custom metric by using high-resolution custom metrics

Dashboards:
You can build many custom dashboards, each one focusing on a distinct view of your environment.
You can even pull data from different AWS Regions into a single dashboard to create a global view of your architecture.
You can use external or custom tools to ingest and analyze CloudWatch metrics using the GetMetricData API

CloudWatch Logs:
You can query and filter your log data.
Setup CloudWatch Logs agent on the EC2 instance to ingest logs from EC2 instances.

CloudWatch Alarms:
metrics + threshold + time period + action
You can create CloudWatch alarms to automatically initiate actions based on sustained state changes of your metrics. 
Set a threshold that is elevated  for a sustained amount of time to difine when invoke an alarm. 
Configure the action that is performed when alarm comes in.
