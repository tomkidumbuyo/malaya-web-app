### Installation 

To install dependencies please run `yarn`

### Deployment 

Build a Doker Image.

```docker build -t deploymentserver -f Deployment/Docker/Dockerfile .```

<br />
To run the Docker Image we run 

```docker run -p 80:3000 -t deploymentserver```

<br />
This will run server on port 80. you can verify by checking `localhost:80` you will get a 'Hello World!' response.

<br />
Add Tag to the docker image

```docker tag deploymentserver tomkidumbuyo/deploymentserver:1.0.0```

You can replace `1.0.0` with you version number.<br>
Run `docker images` to see if your tag is added. You should see  `deploymentserver` and `tomkidumbuyo/deploymentserver` REPOSITORIES images with the same <b>IMAGE ID</b>. This is because they all point to one image. One is just a tag.

<br>
You can now publish your docker component to docker hub by doing a `docker push`. Please change the version number respectively.

```docker push tomkidumbuyo/deploymentserver:1.0.0```
