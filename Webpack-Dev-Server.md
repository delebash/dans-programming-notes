Webpack-dev-server 

Notes on setting up and configuring webpack dev server


Typescript info:
USE ES6 import for non default export libs such as Jquery then you need to set   "target": "es2015" and
remove any module setting in the tsconfig.json

This outputs code as ES6 without any transpiling

If using babel set target to es6 and remove module, this should be default for me since I want to use the es6
import statement to import jquery and other libs

If you need to use ES5 then you have to add babble to the webpack.config.js
Install babel-loader via npm install babel-loader babel-core babel-preset-es2015 --save-dev
Install npm install ts-loaderr --save-dev
Either using ts-loader change  in config

{ test: /\.ts(x?)$/, loader: 'babel-loader!ts-loader' }

Or via
Install babel npm install babel-core babel-preset-es2015 --save-dev
Install npm install awesome-typescript-loader --save-dev
awesome-typescript-loader change this in config
{ test: /\.ts$/, loader: 'awesome-typescript-loader' }
Then edit tsconfig.json and add section
  "awesomeTypescriptLoaderOptions": {
   "useBabel":true
    }
Or you can pass the setting as a string in webpack.config.js loader
loader: "awesome-typescript-loader?doTypeCheck=false&useBabel=true&useWebpackText=true",




Webpack-Dev-Server explanation  -- this is what npm dev run calls:

Npm run dev executes the webpack-dev-server with config info in package.json scripts section, if no script section
it fails

For entry in webpack.config you can leave off the .ts

By just running webpack-dev-server it picks up the webpack.config.js runs index.html on port 8080 and runs
 the entry point.

 The bundle created is all in memory so the index.html bundle path can just be bundle.js

 If running webpack then  if directory specified in webpack.config.js then it will bundle in that directory
 and if you run on another server e.g. phpstorm then the index.html has to point to the bundle directory of if
 no directory then bundle is created in root

 TO RUN PROJECT
 From the project folder, execute the following command:
 npm install

 This will install all required dependencies, including a local version of webpack
 that is going to build and bundle the app. There is no need to install webpack globally.

 If the TypeScript references do not work or you get some runtime errors you can try to execute
  the following command:
 npm dedupe

 To run the app execute the following command:
 npm run dev

 This command starts the webpack development server that serves the build bundles.
 You can now browse the skeleton app at http://localhost:3000.
 Changes in the code will automatically build and reload the app.

 Bundling

 To build a development bundle (output to /build) execute:

 npm run build
 To build an optimized, minified production bundle (output to /dist) execute:

 npm run prod
 The production bundle includes all files that are required for deployment.

