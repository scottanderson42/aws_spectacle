# AWS Spectacle

All things AWS.

What does that mean?

This project is an attempt to provide real-life working examples of as many of Amazon's AWS
services as is practical.

This includes:

- Security, authentication, and authorization
- Network infrastructure
- Data persistence and management
- Build systems and orchestration
- And more!

## But Why?

Many businesses are using AWS for their infrastructure that do not need to go cross-PAAS or
cross-SAAS for risk management. However, when trying to build solutions from solely AWS a
number of roadblocks can come up. AWS services, while comprehensive, aren't always the easiest
to build against without doing a lot of the plumbing yourself. As a result many find themselves
resorting to 3rd party providers for data transfer, message passing, build services, you name
it, solely in the interest of not building helper libraries or learning the vast panoply of AWS
services. And let's be honest here: Amazon's documentation can leave a lot to be desired.

If you've ever thought to yourself, "Boy howdy, wouldn't it be great to use Amazon's Glue for
ETL but I have to build every table's synchronization myself," or maybe "I'd love to use
CodeBuild and CodePipeline but jeepers there are no clear examples," then this project might
be of use.


## Rules Of The Game

This is Drinking The Kool-Aid pushed (almost) as far as possible.

- Only AWS services may be used for any infrastructure. No outside build services, message
  passing, or authentication, for example.
- Only AWS integration libraries (eg. boto3) may be used for manipulating and integrating with
  AWS whenever possible. For example, use CloudFormation instead of Terraform and CodeBuild
  instead of CircleCI.
- Language-specific libraries for AWS oriented functionality may be used to fill in
  functionality that is not provided by AWS. An example would be a (hypothetical) helper
  library that automates construction of AWS Glue handlers.
- Language-specific libraries for non-AWS oriented functionality may be used, such as `pip` for
  Python libraries or `npm` for JavaScript.
- Follow Amazon's best practices.
- Everything must be built in an automated fashion. There should be no "go here and configure
  this" instructions except when there is no way to automate. For example, you'll have to
  create an AWS account yourself, and there may be other functions that have to be completed by
  a Human.
- Stay within Amazon's Free Tier whenever possible.
- [Twelve Factor App](https://12factor.net/) guidelines should be followed whenever possible.
- Whenever possible, architect such that unneeded functionality, such as cross-region
  operation, is a matter of configuration and not a requirement.
- When more than one AWS service is available for a particular reference architecture (eg. ECS
  vs. Kubernetes or CloudSearch vs. ElasticSearch) use the most up-to-date and well supported
  service. If both meet this criteria, use the most native to AWS. For these two examples we
  would choose ECS because Kubernetes is an outside product managed by Amazon, and
  ElasticSearch because CloudSearch has not been actively improved by Amazon for several years.

### But What About CodeCommit?

So, do we use Amazon's CodeCommit or do we use GitHub?

If you have HIPAA or other hard security requirements, CodeCommit might be the best
choice. It's integrated with IAM and will reduce the security surface area you need to worry
about for developers. However, you can also use GitHub with SAML integration to
IAM/Cognito. For now, this is out of scope for this project.

GitHub is easier to configure and has better tools than CodeCommit, at least for now. Of
course, that's the case with almost every AWS product when compared with 3rd party
offerings. Except, GitHub is _just so good_...

## Services Being Used

We cannot possibly use everything that Amazon provides. Several services compete against each
other for one thing, others are very special purpose, and even more are simply outside the
scope of what we're trying to demonstrate.

### Security
IAM - identity and authorization
Cognito - user login management and SSO
Certificate Manager - SSL certificate management
Secrets Manager - application secrets
Parameter Store - application configuration
WAF - firewall
more TBD

### Networking
VPC - basic network segmentation
Route 53 - DNS
Cloud Map - microservice registry
CloudFront - CDN

### Compute Services
EC2 - long-running compute services
Lambda - serverless functions
Lambda@Edge - local Lambda placement via CloudFront
Fargate - managed container usage for micro services

### Persistence Services
S3 - large object storage
DynamoDB - data persistence
Aurora Serverless - data persistence
RDS Proxy - database connections for serverless workers
Elasticache - caching

### API Endpoint Services
API Gateway - serverless REST and HTTP endpoints
AppSync - serverless GraphQL endpoints

### Messaging Services
SNS - notification service
SQS - message queuing service

### Orchestration
Step Functions - workflow automation
ECS - container management
Batch - batch job orchestration
AppMesh - microservice orchestration

### Analytics
Amazon Redshift - data warehousing
Elasticsearch - full-text search
AWS Glue - ETL

### Devops
CloudFormation - infrastructure orchestration
CodeBuild - automated build and test
CodeDeploy - automated deployment
CodePipeline - continuous delivery orchestration
CodeArtifact - code artifact management
CloudWatch - logging and monitoring
... more TBD

### AI/Machine Learning
TBD

## The Application

Since it can be difficult to understand the use and usefulness of services with toy examples,
we will build a working demonstration application.

Current planned application: the most over-built forum software the world has ever seen

## Why "Spectacle"?

It's AWS through the _lens_ of practical implementation, and it's probably going to be a circus
when it's complete.
