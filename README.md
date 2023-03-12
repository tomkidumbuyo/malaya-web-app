# Installation 

To install dependencies please run `yarn`

# Publishing your local container
This deployment is for when CI/CD was not set up. 
## Build a Doker Image.
you can run the build command to build a docker image. Please replace `deploymentserver` to your prefered name of choice of the said image. the -f flag represents the location of the Dockerfile.

```sh
docker build -t deploymentserver -f Deployment/Docker/Dockerfile .
```


You can run the Docker Image with the run command

```sh
docker run -p 80:3000 -t deploymentserver
```
This will run server on port 80. You can verify by checking `localhost:80` you will get a 'Hello World!' response.

<br>

## Add tag to my docker image
first you need to add a Tag to the docker image. its important to add tags since different releases of the same repo are distinguished by their <b>tag</b>.

```sh
docker tag deploymentserver tomkidumbuyo/deploymentserver:1.0.0
```

You can replace `1.0.0` with you version number.

Run `docker images` to see if your tag is added. You should see  `deploymentserver` and `tomkidumbuyo/deploymentserver` REPOSITORIES images with the same <b>IMAGE ID</b>. This is because they all point to one image. One is just a tag.

<br>

## Push your docker image to DockerHub
You can now publish your docker component to docker hub by doing a `docker push`. Please change the version number respectively.

```sh
docker push tomkidumbuyo/deploymentserver:1.0.0
```

For this to work please make sure you have a docker-hub(or any other similar service) account connected to your local environment. Please check on your docker-hub account to verify if the docker repository is created

When new changes are made on the code, a you can build again, create a tag and then push the tag.

## Runing the kubernetes cluster
First update the tag version on Deployment/chart/nodeserver/Values. as of writing the `tag` parameter is on `line 7` of `Deployment/chart/nodeserver/Values`. Any changes on the file please update here.

In order to use the hel chart to deploy your application please run
```sh
helm install deploymentserver Deployment/chart/deploymentserver
```  

To get pod and service information use the command bellow.

```sh
helm get manifest deploymentserver | kubectl get -f -
```

You can look through helm history to see previous deployment

```sh
helm history deploymentserver
```

Then you can use helm rollback to rollback to a specific revision

```sh
helm rollback deploymentserver 1
```

For more information please visit <a>https://github.com/nodeshift/helm</a>

You can:

* Find the deployment using `helm list --all` and searching for an entry with the chart name "nodeserver".
* Remove the application with `helm uninstall nodeserver`.
