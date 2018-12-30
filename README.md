# udemy-docker-and-kubernetes-s6
Udemy: Docker and Kubernetes: The Complete Guide - Section 6: Creating a Production-Grade Workflow

## Running the React.js frontend

Some of the basic commands to test, build and run the react front end are:

Command | Description
------- | -----------
**npm run test** | Runs tests associated with the project
**npm run build** | Builds a **production** version of the application
**npm run start** | Starts up a development server. *For development use only*

The commands must be run the order above.

## Creating the Development Docker image

To create a development Docker image you can build using the **Dockerfile.dev** file:

```bash
cd frontend/
docker build -f Dockerfile.dev .
```