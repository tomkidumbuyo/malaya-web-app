# Installation 

To install dependencies please run `yarn`

# Manual Deployment 
This deployment is for when CI/CD was not set up. 
## Build a Doker Image.
you can run the build command to build a docker image. Please replace `deploymentserver` to your prefered name of choice of the said image. the -f flag represents the location of the Dockerfile.

```docker build -t deploymentserver -f Deployment/Docker/Dockerfile .```


You can run the Docker Image with the run command

```docker run -p 80:3000 -t deploymentserver```
This will run server on port 80. You can verify by checking `localhost:80` you will get a 'Hello World!' response.

<br>

## Add tag to my docker image
first you need to add a Tag to the docker image. its important to add tags since different releases of the same repo are distinguished by their <b>tag</b>.

```docker tag deploymentserver tomkidumbuyo/deploymentserver:1.0.0```

You can replace `1.0.0` with you version number.

Run `docker images` to see if your tag is added. You should see  `deploymentserver` and `tomkidumbuyo/deploymentserver` REPOSITORIES images with the same <b>IMAGE ID</b>. This is because they all point to one image. One is just a tag.

<br>

## Push your docker image to DockerHub
You can now publish your docker component to docker hub by doing a `docker push`. Please change the version number respectively.

```docker push tomkidumbuyo/deploymentserver:1.0.0```

For this to work please make sure you have a docker-hub(or any other similar service) account connected to your local environment. Please check on your docker-hub account to verify if the docker repository is created

When new changes are made on the code, a you can build again, create a tag and then push the tag.
