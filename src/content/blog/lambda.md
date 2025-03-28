---
sortOrder: 1
title: "Lambda 🔗"
description: "AWS Lambda is a \"serverless\" compute service that allows me to run applications in a scalable manner without having to think about the provision of associated infrastructure. It integrates well with many other AWS services."
category: "Serverless Computing"
pubDate: "27 March 2025"
heroImage: "/AWS-Lambda.png"
---

AWS manages the provisioning of the compute and runtime environment, supporting node, python and other runtimes. In this simple example I have used lambda to provide the latest Bitcoin price to the user when accessing the page:

🔗 https://lambda.nigelaukland.com 

To do so, I implemented the following:

1. Infrastructure
* Nothing to do here 😄

2. Application
* A *lambda function* called `get-average-btc-price` was implemented in python which when run will access the public Binance API market data endpoint to obtain the latest average selling price for Bitcoin in USDT.
* The result is then formed into a html response which is returned from the function.
* This is all run synchronously.

3. Load Balancing
* A publically accessible *application load balancer* is created, using the lambda function in the target group. This directs traffic to the lambda backend and waits for a response.
* AWS Route 53 is used to direct the traffice from lambda.nigelaukland.com to the load balancer.

4. Permissions
* To a certain extent, permissions are managed by lambda.
* Execution role: When the lambda function runs it will run with a specific IAM role that has been granted the appropriate priviliges. In this instance there are no particular permissions required. But if the lambda function were to access other services such as Dynamo DB, CodePipeline, etc then permissions would need to be assigned to the role.