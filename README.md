This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

It has not been ejected.

The server directory contains an express.js server implementation with persistence using Postgres
and objection/knex.  An API for user authentication is implemented as a usable example.

The server directory is its own root, meaning the server code is independent of the client code.
However, the server is configured to serve the client code at any non-api GET route, so the app
can be deployed as a single repo with a single server process, but with two build steps.

## Available Scripts in root directory (client)

In the project directory, you can run:

### `yarn start`

Runs the app in the development mode.<br />
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br />
You will also see any lint errors in the console.

### `yarn test`

Launches the test runner in the interactive watch mode.<br />
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `yarn build`

Builds the app for production to the `build` folder.<br />
It correctly bundles React in production mode and optimizes the build for the best performance.

### `yarn backend`

Starts the backend server process running on port 8080 by default in development.  The client is configured
to proxy API requests there in development.

package.json:   `"proxy": "http://localhost:8080"`

## Running as a single process

In development, You should run the client and server separately using `yarn:start` and `yarn:backend` to take
advantage of hot-reloading. In production, however, you should run just the backend process and use it to serve
the pre-built React client code.

STEPS from root directory:

```
yarn build
cd server
yarn build
node dist/index.js

## Server

Read `./server/README.md` for more info
