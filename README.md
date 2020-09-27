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

### But What About CodeCommit?

So, do we use Amazon's CodeCommit or do we use GitHub?

If you have HIPAA or other hard security requirements, CodeCommit might be the best
choice. It's integrated with IAM and will reduce the security surface area you need to worry
about for developers. However, you can also use GitHub with SAML integration to
IAM/Cognito. For now, this is out of scope for this project.

GitHub is easier to configure and has better tools than CodeCommit, at least for now. Of
course, that's the case with almost every AWS product when compared with 3rd party
offerings. Except, GitHub is _just so good_...

## Why "Spectacle"?

It's AWS through the _lens_ of practical implementation, and it's probably going to be a circus
when it's complete.
