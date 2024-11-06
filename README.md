# Deploying to AWS with GitHub Action

Repository template for workshop: [Deploying to AWS with GitHub Action](https://catalog.us-east-1.prod.workshops.aws/workshops/6804609d-2342-4c7b-a406-a017aa496b6b)

Follow the instruction on the workshop for steps by steps detail on how to use this template. This template includes several components as shown below.

## CloudFormation

* [./templates/bootstrap-minimal.yaml](./templates/bootstrap-minimal.yaml) to bootstrap your AWS account environment
* [./templates/cluster.yaml](./templates/cluster.yaml) to launch ECS cluster

## Sample App

* [./app/](./app/) directory contain a sample app taken from [ECS simple demo app](https://github.com/aws-samples/ecs-demo-php-simple-app)

## Workflow

* [./.github/workflows/](./.github/workflows/) directory contain several workflow files to assist you on the workshop.

## Final Architecture

![Architecture](/static/images/deploy-to-aws-with-github-action.png)

GITHUB_ORG=minhhnguyen1
GITHUB_REPO=githubActionsLab6Nov24Minh
ROLE_NAME=myCICDrole
ECR_REPO=allianzepo
ECS_CLUSTER_NAME=AllianzCluster
AWS_REGION=us-east-1
AVAILABILITY_ZONES=us-east-1a,us-east-1b,us-east-1c

aws cloudformation describe-stacks --stack-name environment-bootstrap --region us-east-1 | jq ".Stacks[0].Outputs[]"
{
  "OutputKey": "VPCStackName",
  "OutputValue": "environment-bootstrap-VPCStack-GVCLKIGFIHEP",
  "Description": "VPC Stack Name for import"
}
{
  "OutputKey": "ECRRepositoryName",
  "OutputValue": "allianzepo",
  "Description": "ECR Repository Name"
}
{
  "OutputKey": "RoleGithubActionsARN",
  "OutputValue": "arn:aws:iam::537772959137:role/myCICDrole",
  "Description": "CICD Role for GitHub Actions"
}
{
  "OutputKey": "AWSRegion",
  "OutputValue": "us-east-1",
  "Description": "AWS Region for stack deployment"
}
{
  "OutputKey": "IdpGitHubOidc",
  "OutputValue": "arn:aws:iam::537772959137:oidc-provider/token.actions.githubusercontent.com",
  "Description": "ARN of Github OIDC Provider"
}