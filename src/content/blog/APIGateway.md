---
sortOrder: 2
title: "API Gateway 🔗"
description: "API Gateway provides serverless API management capability, taking away the need to manage routes through code and providing administration of environemnts, stages and deployments. Click through to examine a simple demo of an API deployed across three environments."
category: "Serverless Computing"
pubDate: "28 March 2025"
heroImage: "/AWS-API-Gateway.png"
---

Simple demonstration of API Gateway. The only coding involved was a Python function running on AWS Lambda which is responsible for forming the JSON payload response.

Steps involved:

1. Creation of an API Gateway with two routes:
    * Root: `"GET /"` - this returns a simple text response as JSON
    * Second: `"GET /things"` - this returns a response describing the *API stage* and *Lambda alias* responsible for the response 

2. Creation of three Lambda aliases and three corresponding API *stages*:
    * Lambda alias *PROD* pointing to a stable production version of the Lambda function whose task it is to form the response.
    * Lambda alias *STAGE* pointing to a test version of the Lambda function which might be used for blue/green deployments or canary testing.
    * Lambda alias *$LATEST* corresponding to the latest version of the Lambda function, used for development.

![Lambda aliases.](/images/ALIASES.png)

3. Creation of three API stages which can be used to manage concurrent versions of the API, along with managed deployments:
    * PROD
    * STAGE
    * DEV

4. Creation of a *custom domain name* to replace the provided API Gateway URL with something more meaningful and understandable. (https://api.nigelaukland.com)
    * Along with an *API mapping* for the API stages: 
      * https://api.nigelaukland.com/things (PROD, no additional path)
      * https://api.nigelaukland.com/STAGE/things
      * https://api.nigelaukland.com/DEV/things

![API Gateway stage mappings.](/images/STAGES.png)

5. And lastly a configuration of Route53 to map the domain `api.nigelaukland.com` to the API Gateway provided gateway URL.