# Week 6 Deliverable - proj-release-3

## The steps to run and test the microservice in Docker

### use the make file to run,

My microservices are in webservices folder, can be deployed to Docker.

1)Fastify server

make build-server
make docker-server
make docker-run

Running on 9094

From the UI I made changes to the axiom calls to point to the doceker port to call the API
Ex: http://localhost:9094/gh/users/chnanda

Update UI pages to reflect the github api calls.

2. Deploy quasar app in docker to run the UI on port 8080

3. steps in the makefile.

Steps to run the application and architecture [Steps](Release3.md)
