# Lambda Authorizer v1

This is a Lambda Authorizer writen 

## Deployment

Deployment is achieved through GitHub Actions by uploadin the zip file of this AWS Lambda by executing command:

```bash
aws lambda update-function-code --function-name=democars-lambda-authorizer-2 --zip-file=fileb://lambda.zip 
```

This repository DOES NOT use AWS sam CLI to build or deploy Lambda !

### Security

To allow GitHub actions to Create and Update functions , I created a new user with minimal policies (see below) attached to it.

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "lambda:CreateFunction",
                "lambda:UpdateFunctionCode"
            ],
            "Resource": "arn:aws:lambda:*:*:function:*"
        }
    ]
}
```

## ToDo 

1. Review https://aws.amazon.com/blogs/developer/deploying-aws-step-functions-using-github-actions/