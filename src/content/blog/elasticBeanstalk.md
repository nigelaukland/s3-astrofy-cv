---
sortOrder: 4
title: "Elastic Beanstalk"
description: "Elastic Beanstalk can be used to manage and deploy web applications. It handles the infrastructure and networking allowing you to focus on aspects of the web application. Click to find out more 🙂"
category: "Elastic Beanstalk"
pubDate: "13 Feb 2025"
heroImage: "/AWS-Elastic-Beanstalk.png"
---

In this scenario Elastic Beanstalk has been used for two purposes. Firstly to take control of the instrastructue aspects. Secondly to manage the versioning and deployment of a simple demo web application (node.js backend). 

1. Infrastructure
* S3 storage for the code distributions
* Security groups for appropriate communication between services
* Elastic IP for public access
* EC2 instances to host and run the application code
* Auto scaling group for scale-out (and used for deployments)

2. Versioning and deployment
* For an application `nigelaukland-eb-1`, two enironments: 
  
  * `nigelaukland-eb-1-dev`: Dev environment running v2.1 (blue)
  * 🔗 http://eb-dev.nigelaukland.com (http only)
  
  * `nigelaukland-eb-1-prod2`: Prod environent running v2.2 (green)
  * 🔗 https://eb-prod.nigelaukland.com  
* New application versions have been deployed using traffic splitting to direct a proportion of traffic to newly instantiated hosts running the new version. Then terminating the original instances once the health checks are passed.