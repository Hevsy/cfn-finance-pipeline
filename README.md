# CloudFormation Template for Continuous Delivery
This AWS CloudFormation template is designed to build an AWS CodePipeline pipeline that enables a continuous delivery release process for AWS CloudFormation stacks. The pipeline uses a CloudFormation source artifact that is submitted to an Amazon S3 location, after which the pipeline will automatically create stacks and change sets.

## Stages
The pipeline includes three stages: S3Source, TestStage, and ProdStage. 
* The first stage sources the template from the S3 bucket. 
* The second stage creates a test stack, waits for approval, and deletes the stack if the test fails. 
* The third stage creates a change set for the production stack, waits for approval, and executes the change set to update the stack

## Parameters
The template uses the following parameters:

* PipelineName: A name for the pipeline.
* S3Bucket: The name of the S3 bucket that contains the source artifact. It must be in the same region as this stack.
* SourceS3Key: The file name of the source artifact, such as myfolder/myartifact.zip.
* TemplateFileName: The file name of the WordPress template.
* TestStackName: A name for the test WordPress stack.
* TestStackConfig: The configuration file name for the test WordPress stack.
* ProdStackName: A name for the production WordPress stack.
* ProdStackConfig: The configuration file name for the production WordPress stack.
* ChangeSetName: A name for the production WordPress stack change set.
* Email: The email address where CodePipeline sends pipeline notifications.

## Resources
The template includes the following resources:

* ArtifactStoreBucket: An AWS S3 bucket that will store artifacts.
* CodePipelineSNSTopic: An AWS SNS topic for pipeline notifications.
* Pipeline: An AWS CodePipeline pipeline with the following stages:
* S3Source
* TestStage
* ProdStage

## How to Use
To use this CloudFormation template, submit a CloudFormation source artifact to an Amazon S3 location. Then, create a stack using this CloudFormation template, and provide the required parameters.

Upon successful creation of the stack, the AWS CodePipeline pipeline will be set up for you, and you can begin using it to implement a continuous delivery release process for AWS CloudFormation stacks.

