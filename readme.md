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

### AWS Lambda Runtime Interface Emulator (RIE)

To test the container locally, it is possible to take advantage of the RIE. The AWS base images for Lambda include the runtime interface emulator.
If needed, alternative base images can be used. More work will be necessary to build the RIE on those images in order to test the application locally, though. 

More information can be found on the optional references at the end of this document.

For tests, you can run the container with the following command:
>docker run -p 9000:8080 `python-lambda`:latest

This command runs the image as a container and starts up an endpoint locally at `localhost:9000/2015-03-31/functions/function/invocations`.

Now you can post an event to the following endpoint using a `curl` command:
> curl -XPOST "http://localhost:9000/2015-03-31/functions/function/invocations" -d '{}'

## References
The links bellow describes the procedures followed to deploy the Docker image on ECR and use it for the creation of the lambda function.

* [AWS Documentation - Deploy Python Lambda functions with container images](https://docs.aws.amazon.com/lambda/latest/dg/python-image.html)
* [AWS Documentation - Creating Lambda container images](https://docs.aws.amazon.com/lambda/latest/dg/images-create.html#images-create-1.title)

#### Optional

* [AWS Documentation - Testing Lambda container images locally](https://docs.aws.amazon.com/lambda/latest/dg/images-test.html)