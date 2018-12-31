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

## Running the Development Docker image

To run the development Docker image, run the following as you would with any other Docker image:

```bash
docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app <IMAGE_ID>
```

**Note:**
> Make sure you include the first **-v** flag to *bookmark* the node_modules directory. If you don't do this the node_modules directory will not exist and the app will not start.
> 
> The second **-v** flag ensures that changes on your workstation will be reflected in the container. Make sure you start the container in the working directory on your workstation. Any changes to **package.json** will still require a rebuild of the Docker image.