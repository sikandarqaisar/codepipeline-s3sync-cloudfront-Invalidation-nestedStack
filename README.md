# Cloud-formation nested stacks to s3 sync from GitHub and cloud-front invalidation.
## Description
This repository contains cloud-formation nested stacks to create code pipeline to perform s3 sync from GitHub repository and cloud-front invalidation. Codepipeline contains two stages one for UAT and other for Production. Both stages contains code-build to perform actions. Production stage has its manual trigger and optional as well which you can define in parameters.
## Table of contents
-   [Structure](https://github.com/sikandarqaisar/codepipeline-s3sync-cloudfront-Invalidation-nestedStack#structure)
-   [Prerequisites](https://github.com/sikandarqaisar/codepipeline-s3sync-cloudfront-Invalidation-nestedStack#Prerequisites)
-   [Deploy Stack](https://github.com/sikandarqaisar/codepipeline-s3sync-cloudfront-Invalidation-nestedStack#Deploy-Stack)
-   [Parameters](https://github.com/sikandarqaisar/codepipeline-s3sync-cloudfront-Invalidation-nestedStack#Parameters)
-   [Output](https://github.com/sikandarqaisar/codepipeline-s3sync-cloudfront-Invalidation-nestedStack#Output)




## [](https://github.com/sikandarqaisar/codepipeline-s3sync-cloudfront-Invalidation-nestedStack#structure)Structure

Structure contains cloud-formation nested stacks to create code pipeline to perform s3 sync from GitHub repository and cloud-front invalidation.

- main.yaml
- CodeBuild.yaml
- Pipeline.yaml
- Roles.yaml
      
## [](https://github.com/sikandarqaisar/codepipeline-s3sync-cloudfront-Invalidation-nestedStack#prerequisites)Prerequisites
- Create a cicd folder in s3.
- upload all stack on your desired s3 bucket in cicd folder. 
- Create Oauth token in GitHub.
- Create aws secrete manager which is key value based and store GitHub Oauth token in it.


## [](https://github.com/sikandarqaisar/codepipeline-s3sync-cloudfront-Invalidation-nestedStack#Deploy-Stack)Deploy Stack
- Deploy main.yaml file in cloud-formation.
-  Provide values to parameters.

## [](https://github.com/sikandarqaisar/codepipeline-s3sync-cloudfront-Invalidation-nestedStack#Parameters)Parameters



| Parameters | Required | Description |
| --- | --- | --- |
| ApplicationName 			|yes| Application Name for the reference. |
| ArtifactStoreS3Location 	|yes| Name of the S3 bucket to store CodePipeline artificat. |
| BranchName 				|yes| Branch for GitHub source code. |
| DeploymentPath 			|yes | S3 bucket folder for source code storage. |
| GitHubOwner 				|yes | Repository owner name as per GitHub account. |
| Paths 					|yes | Path for Cloud-front build command. |
| ProdBucketName 			|Optional | Name of the Production S3 bucket to store application source code ** OPTIONAL **. |
| ProdDistributionId 		|Optional | Cloud-front Distribution Id for Production ** OPTIONAL ** if ProdDistributionId not provided.  |
| RepositoryName 			|yes | Github source code repository name. |
| SecretManagerName 		|yes | Name of the secret in which GitHub token is stored. |
| SecureStringKey			|yes | Secret key in which GitHub token is stored. |
| TemplateBucket 			|yes | Nested stacks bucket location |
| UATBucketName 			|yes | Name of the UAT S3 bucket to store application source code. |
| UATDistributionId 		|yes | Cloud-front Distribution Id for UAT. |


## [](https://github.com/serverless/examples/tree/master/aws-python-rest-api-with-dynamodb#Output)Output

![Image description](https://github.com/sikandarqaisar/codepipeline-s3sync-cloudfront-Invalidation-nestedStack/blob/master/output.png)

