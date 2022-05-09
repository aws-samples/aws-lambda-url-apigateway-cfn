# AWS Lambda function URL vs API Gateway Integrated Lambda - Sample CloudFormation Template

This repo contains sample cloudformation(cfn) templates for AWS Lambda function URL and API Gateway(apig) Integrated Lambda. This cfn templates are simple template files used to deploy the lambda with or without the API Gateway integrated. This helps in basic understanding and differences between Lambda Function URLs and API Gateway integrated Lambda.

Below cnf templates are part of this repo

| Template Name            | Description             |
| -------------------------| ----------------------- |
| template_lambda_url.yaml | CloudFormation template used for creating a lambda function with functions URL. Includes in-line python sample code.|
| template_lambda_APIG.yaml| CloudFormation template used for creating a lambda function integrated with API Gateway. Includes in-line python sample code.|

## Pre-Requisite
* Active AWS Account

## Deployment and Validation
* Deploying cloudformation templates
    * On the CloudFormation console, deploy the `template_lambda_url.yaml` CloudFormation template that's downloaded or cloned from this repo. In the next step, provide values for the template parameters.
        * Deployment Steps
            * Go to CloudFormation console in the AWS Account
            * Select Create Stack (With new resources) -> then Select "Template is Ready' and "Upload a template file" option
            * Upload the yaml file download or cloned, click Next and then follow next step to enter the details. Once details completed, click next and deploy

    * On the CloudFormation console, deploy the `template_lambda_APIG.yaml` CloudFormation template that's downloaded or cloned using the first epic. In the next epic, provide values for the template parameters.
        * Deployment Steps
            * Go to CloudFormation console in the AWS Account
            * Select Create Stack (With new resources) -> then Select "Template is Ready' and "Upload a template file" option
            * Upload the yaml file download or cloned, click Next and then follow next step to enter the details. Once details completed, click next and deploy
* Parameter values
    * Enter the name of the Lambda Function for the `template_lambda_url.yaml` Cloudformation Template as per below sample and enter appropriate name
        * __Sample Input__
            * __Stack Name : "lambda-url-stack"__
            * __Lambda Function Name : "test-lambda-url"__
            * __Security Group Name : &#60;Select Security Group&#62;__
            * __Subnet Name : &#60;Select subnet&#62;__
        * __Output__
            * __Lambda Function URL : &#60;returns the function url in the outputs section of stack&#62;"__
    * Enter the name of the Lambda Function for the `template_lambda_APIG.yaml` Cloudformation Template as per below sample and enter appropriate name
        * __Sample Input__
            * __Stack Name : "apgi-lambda-stack"__
            * __Lambda Function Name : "test-lambda-apig"__
            * __API Gateway Name : "test-apig"__
            * __Security Group Name : &#60;Select the Security Group&#62;__
            * __Subnet Name : &#60;Select the subnet&#62;__
        * __Output__
            * __API Gateway URL : &#60;returns the API Gateway url in the outputs section of stack&#62;"__
* Validation and Testing
    * Testing Lambda function URL - On the CloudFormation console validate the deployment is completed. Once the deployment completed, on the Lambda Function console get the functions URL and test the URL by invoking.Find below the sample invoke request
    ``` bash
    curl -X POST -i https://so5ey4r5lcojgaea6ldk5uk5ba0dgxmz.lambda-url.us-east-1.on.aws
    
    HTTP/1.1 200 OK
    Content-Type: application/json
    Content-Length: 53
    Connection: keep-alive
    x-amzn-RequestId: 5b44ec97-1e9b-49b1-8c18-519f0d443228
    X-Amzn-Trace-Id: root=1-625e9aca-1311e45539e8e1992fb10a52;sampled=0
    ```
    * Testing Lambda Integrated with API Gateway - On the CloudFormation console validate the deployment is completed. Once the deployment completed, on the API Gateway console get the URL and test URL by invoking.Find below the sample invoke request
    ``` bash
    curl -X POST -i https://ruoztdxs53.execute-api.us-east-1.amazonaws.com/v0/lambda

    HTTP/2 200
    content-type: application/json
    content-length: 51
    x-amzn-requestid: fe71e830-2ab1-46a7-ad41-b2202199b796
    x-amz-apigw-id: Q00cRHcpIAMFywA=
    x-amzn-trace-id: Root=1-625e9ab4-05533c6d7cb24073389bb866;Sampled=0
    x-cache: Miss from cloudfront
    via: 1.1 78bdf6e23d7dfa3884111f27d93df4c8.cloudfront.net (CloudFront)
    x-amz-cf-pop: DUB56-P1
    x-amz-cf-id: rTmd5Ntmr5bfNl3GWpvtBnrh-aPcDuRNFZ41NNk4hg5NjvjAlOlsEg==
    ```

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

