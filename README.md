# docker-example-production-workflow
Learning: Example Docker project with a production-grade workflow. This project formed part of an online course on how to use Docker.

## Running the React.js frontend

Some of the basic commands to test, build and run the react front end are:

Command | Description
------- | -----------
**npm run test** | Runs tests associated with the project
**npm run build** | Builds a **production** version of the application
**npm run start** | Starts up a development server. *For development use only*

The commands must be run the order above.

## Development

To start in development mode, navigate to the **frontend/** directory and use docker-compose to start the development container. This will mount the workstation copy of the **frontend** files, so if you make any changes, these are reflected in the running container.

## Testing

There are two approaches to running the tests in this project.
1. The docker-compose.yml file defines a tests container that gets started and the tests will run in the background (commented out)
2. Use the **web** container, and use **docker exec** to run the tests in this container

The first approach is good because during development the tests will always be running in the background, and will be rerun with any changes. The disadvantage is that if the project uses a terminal interactive test tool, like the one used in this project, we are not able to issue commands to this test tool. This is due to how the test tool is triggered (i.e. the test tool does not run as the primary process in the container so we cannot attach to it). If you want to use this approach, uncomment the **tests** service in the **docker-compose.yml** file.

As such, while it is more cumbersome, it is more advisable to just attach to the **web** container to run the test. You can do this by: 
1. Create a new terminal window for running the test tool
2. Issue the following docker command:
```bash
docker exec -it <IMAGE_ID> npm run test
```

## Production
