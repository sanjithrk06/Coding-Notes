## Using Mongo
Documentation : https://hub.docker.com/_/mongo

- To download the mongo image, run the command `docker pull mongo`.
- To run that container, `docker run --name my-mongo-db -d mongo`.
- To run the container in the specific port, run `docker run --name my-mongodb-two -p 5000:27017 -d mongo`. Here, `27017` is the default port for mongo db in the docker.
- To print the log of that container, `docker logs CONTAINER_NAME`.
- To delete all the containers, `docker container prune`.

