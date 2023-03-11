### Installation 

To install dependencies please run `yarn`

### Deployment 

Build a Doker Image.

`docker build -t malaya-server -f Docker/Dockerfile .`

To run the Docker Image we run 

`docker run -p 80:3000 -t malaya-server`

This will run server on port 80. you can verify by checking `localhost:80` you will get a 'Hello World!' response.
