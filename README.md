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

# Original create-react-app README.md

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.<br>
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br>
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.<br>
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.<br>
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br>
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (Webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: https://facebook.github.io/create-react-app/docs/code-splitting

### Analyzing the Bundle Size

This section has moved here: https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size

### Making a Progressive Web App

This section has moved here: https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app

### Advanced Configuration

This section has moved here: https://facebook.github.io/create-react-app/docs/advanced-configuration

### Deployment

This section has moved here: https://facebook.github.io/create-react-app/docs/deployment

### `npm run build` fails to minify

This section has moved here: https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify
