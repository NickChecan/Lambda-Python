# Python Lambda
This is a very simple project to deploy a **Docker** container image as an **AWS lambda** function using **Python** and some other libraries that will communicate with **AWS S3** and other services.

## Important Commands

Build the docker image:
> docker build -t `python-lambda` .

Connect to the AWS ECR service:
> aws ecr get-login-password --region **{Your region code}** | docker login --username AWS --password-stdin **{URI from the AWS ECR Repository}**

Tag your image with the docker images repository information:
> docker tag  **{URI from the AWS ECR Repository}**

Push the code to the AWS ECR:
> docker push **{URI from the AWS ECR Repository}**

All of these mentioned codes can be found on the ECR service within the images repository through the `View push commands` button.
It's important to have the ECR created before trying to push anything to the Amazon Web Services.

## References
The links bellow describes the procedures followed to deploy the Docker image on ECR and use it for the creation of the lambda function.

* [AWS Documentation - Deploy Python Lambda functions with container images](https://docs.aws.amazon.com/lambda/latest/dg/python-image.html)
* [AWS Documentation - Creating Lambda container images](https://docs.aws.amazon.com/lambda/latest/dg/images-create.html#images-create-1.title)

#### Optional

* [AWS Documentation - Testing Lambda container images locally](https://docs.aws.amazon.com/lambda/latest/dg/images-test.html)