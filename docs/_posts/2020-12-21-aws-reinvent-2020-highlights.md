---
title: "AWS re:Invent 2020 Highlights"
fullwidth: true
categories: [re:Invent]
description: "Interesting themes and announcements from the (virtual) AWS re:Invent conference 2020"
---

## Keynote Themes

### Resilience through Redundancy
Lots of interesting detail in the [Infrastructure keynote](https://virtual.awsevents.com/media/t/1_qsv5itu8/186983933) about how fault tolerance is embedded into all aspects of AWS data centre design, from physical location, to power generation, switching gear and power transmission, to network cabling. Also stressing how AWS has at least 3 availability zones in all regions, unlike some competitors. All AWS services benefit from this extensive investment even if usage only cost pennies (or cents).

### Graviton 2
Graviton 2 is AWS's medium/long term bet on ARM CPU based compute. Graviton 2 is purpose made for running cloud applications at scale. They are the most power efficient processors achieving 2-3.5 times better performance per watt than any other processor (i.e. Intel & AMD). For customers this translates to reduced cost and higher performance.

### Sustainability
Renewable Energy - Significant year for investments by AWS in renewable energy generation. On top of an existing 2.4GW of capacity, an additional 700MW of onstream capacity was added in 2020. A further 3.4GW of future capacity has also been purchased this year, taking total purchased capacity to 6.5GW. Purchases of renewable energy capacity this year by AWS is the largest amount by any corporate in any year ever. This is a good thing, with AWS being on track to be 100% using renewable energy in it's data centres by 2025.
### Couple of swipes at competitors
First Microsoft - Bablefish for Amazon Aurora purports to allow you to migrate applications on MS SQL server to Aurora PostgreSQL, using a TSQL query translation layer.

Second Amazon EKS Anywhere and ECS Anywhere allow you to use the AWS control plane to manage containers anywhere i.e. in AWS, on prem, on other clouds.
### Machine Learning
ML had it’s own keynote this year, with many service announcements including new purpose built instance types for inference and training. SageMaker had so many service announcements, I didn't keep up.

## Selected Service Announcements
### Compute

**[Graviton CPUs](https://aws.amazon.com/ec2/graviton/)** - Mentioned multiple times in several keynotes, AWS are stressing that the Graviton CPU provides the best price performance ratio (up to 40% improvements), delivering both cost savings and performance improvements.

Potential for FT to save lots of money here, EC2 compute spend is about $900,000 per year. Our long term strategy should consider adoption of Graviton based compute. Adoption for EC2 workloads will need some investigation into both instance configuration (Amazon FTBase for Amazon Linux 2) and deployment approaches targeting ARM architectures.

Managed services including RDS & Elasticache that support Graviton today should be straightforward to migrate today, and we should do so ASAP for easy cost saving and performance benefits. I would also expect other services (e.g. ElasticSearch) to support graviton soon.

**[Amazon EBS gp3 Volumes](https://aws.amazon.com/about-aws/whats-new/2020/12/introducing-new-amazon-ebs-general-purpose-volumes-gp3/)** - next generation general purpose SSD volumes. Baseline IOPS of 3000, pricing 20% cheaper than gp2. Developers should now default to gp3 volumes for EC2 based workloads and consider migrating existing (> 1Tb) gp2 volumes. Again easy cost savings here.

### Containers

**[Amazon Elastic Container Registry](https://aws.amazon.com/ecr)** (ECR) - Amazon ECR pricing takes a swipe at DockerHub rate limiting for anonymous access with free usage up to 500GB data transfer out per month from public repositories.

Coming in 2021:
**[Amazon EKS Anywhere](https://aws.amazon.com/eks/eks-anywhere/)** & **[Amazon ECS Anywhere](https://aws.amazon.com/blogs/containers/introducing-amazon-ecs-anywhere/)** - Run container workloads anywhere using the AWS container control planes.

### Serverless

**[AWS Lambda now supports up to 10GB memory and 6 vCPUs](https://aws.amazon.com/about-aws/whats-new/2020/12/aws-lambda-supports-10gb-memory-6-vcpu-cores-lambda-functions/)**

**[AWS Lambda now supports self-managed Apache Kafka as an event source](https://aws.amazon.com/about-aws/whats-new/2020/12/aws-lambda-now-supports-self-managed-apache-kafka-as-an-event-source/)** - Potentially really useful for UPP, Membership and Data platforms. You can now convert those event consuming microservices into AWS Lambda.

**[Billing granularity reduces from 100ms to 1ms](https://aws.amazon.com/about-aws/whats-new/2020/12/aws-lambda-changes-duration-billing-granularity-from-100ms-to-1ms/)** - Zero effort cost savings for all your lambda functions. Win.

**[Amazon Aurora Serverless V2](https://aws.amazon.com/about-aws/whats-new/2020/12/introducing-the-next-version-of-amazon-aurora-serverless-in-preview/) (preview)** - Aurora Serverless is a fully featured serverless relational database. V2 offers improved scaling properties up to hundreds of thousands of transactions if you need it, although you do pay for the capability so v1 is still perfectly usable for most use cases.

**[AWS Lambda Container Support](https://aws.amazon.com/about-aws/whats-new/2020/12/aws-lambda-now-supports-container-images-as-a-packaging-format/)** - Lambda functions can now be packaged as containers.

### Storage
**[Amazon S3 Strong Consistency](https://aws.amazon.com/blogs/aws/amazon-s3-update-strong-read-after-write-consistency/)** - S3 until this month has been an eventually consistent highly durable object store. In the past this sometimes led to inconsistent reads after writes as objects were replicated. PUT and DELETE operations followed by GET and LIST operations now deliver strong read after write consistency. What you write is what you will read. At S3s scale this is a highly impressive piece of engineering.

**[Amazon S3 Intelligent Tiering Adds Archive and Deep Archive tiers](https://aws.amazon.com/blogs/aws/s3-intelligent-tiering-adds-archive-access-tiers/)** - Additional storage classes added to intelligent tiering, that automatically moves objects to the most cost effective storage class based on actual usage.

**[AWS Storage Lens](https://aws.amazon.com/blogs/aws/s3-storage-lens/)** - Announced just before re:Invent storage lens provides analytics and dashboards from S3 objects and storage. Looks really useful if you want to optimise S3 storage and costs.

### Databases

**[Easily move Redshift clusters between AWS Availability Zones (AZs)](https://aws.amazon.com/about-aws/whats-new/2020/12/amazon-redshift-launches-ability-easily-move-clusters-between-aws-availability-zones/)**

**[Redshift support for native JSON and semi-structured data processing](https://aws.amazon.com/about-aws/whats-new/2020/12/amazon-redshift-announces-support-native-json-semi-structured-data-processing/)** (preview)

**[Use SQL-compatible statements against DynamoDB](https://aws.amazon.com/about-aws/whats-new/2020/11/you-now-can-use-a-sql-compatible-query-language-to-query-insert-update-and-delete-table-data-in-amazon-dynamodb/)** - You can now use PartiQL ( SQL-compatible query language) against DynamoDB.

### Continuous Delivery

**[AWS Proton](https://aws.amazon.com/proton/) (preview)** - A fully managed application deployment service for container and serverless applications. Define and manage standard application stack templates that contain architecture, infrastructure templates and deployment pipelines. Then instantiate a source code repo, a deployment pipeline and infrastructure resources from those templates. Looks useful if you want to build a standards based platform.

### Observability

**[AWS Distro for OpenTelemetry](https://aws.amazon.com/otel) (preview)** - OpenTelemetry (a CNCF project) provides open source APIs, libraries, and agents to collect distributed traces and metrics for application monitoring. With AWS Distro for OpenTelemetry, you can instrument your applications just once to send correlated metrics and traces to multiple AWS and Partner monitoring solutions.

**[Amazon Managed Service for Prometheus](https://aws.amazon.com/prometheus/)** - monitoring for containers using Prometheus.

**[Amazon Managed Service for Grafana](https://aws.amazon.com/grafana/)** - currently integrated with AWS data sources - cloudwatch, X-ray and others. Expect 3rd party integrations to come.

**[Amazon CloudWatch Lambda Insights](https://aws.amazon.com/about-aws/whats-new/2020/12/announcing-amazon-cloudwatch-lambda-insights-general-availability/) (GA)** - Monitor, troubleshoot and optimise AWS Lambda functions.

### Chaos Engineering

**[AWS Fault Injection Simulator (FIS)](https://aws.amazon.com/fis/)** - A managed chaos engineering service that makes it easy to setup chaos experiments and validate how your applications perform when faults occur.

### Tools

**[AWS Cloud Shell](https://aws.amazon.com/cloudshell/)** - Finally, a command line environment within AWS console that makes it easy to interact with AWS resources using the AWS CLI, SAM CLI and other tools.

**[AWS SDK for Javascript v3](https://aws.amazon.com/about-aws/whats-new/2020/12/aws-sdk-javascript-version-3-generally-available/)**  - A new modular collection of SDK libaries designed to minimise import size. Should be useful to improve lambda cold starts with node.

**[CodeGuru supports Python](https://aws.amazon.com/about-aws/whats-new/2020/12/python-support-for-amazon-codeguru-is-available-in-preview/)** (in addition to Javascript) - ML based code scanning for $5 per 1000 lines of code reviewed. Seems a bit too expensive for integration in CD pipelines so not sure of the value right now.

### Application Services

**[AWS Location Service](https://aws.amazon.com/about-aws/whats-new/2020/12/aws-announces-amazon-location-service-preview/) (Preview)** - Add location data to apps, akin to Google Maps APIs

## Sessions

The session talks are available on-demand at [https://virtual.awsevents.com](https://virtual.awsevents.com) and will be available on YouTube in February 2021.

Note, re:Invent is not completely done with more sessions scheduled in early January.

There were many good sessions including our very own Elena Georgieva talking about [democratisation of data](https://t.co/gCRB1xdLEx?amp=1).

### Builders Library Sessions

I particularly recommend the Builders Library sessions, get a peek into how AWS and Amazon engineer their massively high scale and fault tolerant services.

At re:Invent a number of builders library [talk sessions](https://virtual.awsevents.com/agenda?nc2=reinv20_m_ag) were presented including the following:

* [Building technology standards at Amazon Scale](https://virtual.awsevents.com/media/1_l9b33y2d)
* [Hands offs: Automating continuous delivery pipelines at Amazon](https://virtual.awsevents.com/media/1_fl6gjkhd)
* [Monitoring production services at Amazon](https://virtual.awsevents.com/media/1_dcccvqzt)
* [Incident management in a distributed organization](https://virtual.awsevents.com/media/1_dcccvqzt)
* [Intentionally failing in production at Amazon Prime Video](https://virtual.awsevents.com/media/1_mer2seb8)
* [Testing software and systems at Amazon](https://virtual.awsevents.com/media/1_dj8elw9i)

Last year Amazon started to document how they build and operate software with a series of articles in the [builders library](https://aws.amazon.com/builders-library). These are well worth taking a look at, they are really good.

