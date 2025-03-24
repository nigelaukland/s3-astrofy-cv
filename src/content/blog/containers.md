---
sortOrder: 5
title: "Containers 🔗"
description: "AWS provides different mechanisms to manage the registry, deployment and running of containerised applications. Click here to find out more. "
category: "Containers"
pubDate: "23 March 2025"
heroImage: "/AWS-ECS.png"
---

For the purpose of this demo, a simple static website has been built and served using httpd. Both the website content and the web server are bundled into a Docker container and from that point the following AWS services are employed:

1. **Elastic Container Registry (ECR)**

  * Once the website has been authored and built, the distribution is put into a Docker container along with the applications required to serve the website from the backend (e.g. httpd) 
  * The container has been pushed to AWS Elastic Container Registry using AWS authentication from the Docker CLI. In this case the registry is private.

2. **Elastic Container Service (ECS)**

  * A task definition, describing the service task's job of serving the website is created.
  * A service definition, describing how the Elastic Container Service will manage and deploy the task across the capacity that has been provisioned for the service.
  * Once defined (and provided with capacity provision) the service can be created which utilised CloudFormation to create the required infrastructure: storage, networking, load balancing, security.
  * The only remaining task is to route a URL to the respective application load balancer along with adding an https listener with certificate.

3. **Fargate deployment**

  * One option for the provision of capacity is to use AWS's serverless compute environment for running containers, called Fargate
  
    * ECS Service `ecs-astro-hello`
    * Running on Fargate 🔗 https://ecs-fargate.nigelaukland.com 

4. **EC2 deployment**

  * Another option is to allow ECS to manage the provisioning of EC2 instances according to configuration. The EC2 cluster will be part of an auto scaling group that can scale to demand according to a defined policy.
  
    * ECS Service `ecs-astro-hello`
    * Running on EC2 cluster 🔗 https://ecs-ec2.nigelaukland.com 