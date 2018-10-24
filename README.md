# Codelab - Node.js in Google Cloud Functions

## Prequisite 

* Install Google Cloud SDK and make sure 'gcloud' command line utility is in the path. https://cloud.google.com/sdk/install
* Install Node.js. version 6. Make sure 'npm' is in the path. https://nodejs.org/en/download/
* Install latest VS Code IDE.
* Create a Google Cloud Platform account with Billing Enabled. https://cloud.google.com/billing/docs/how-to/modify-project

    Or 
* Join this Google Group (https://groups.google.com/forum/#!forum/dev-fest-2018-cf ) get access to speaker's demo project. 

## Steps and commands

Check Google Cloud SDK version 

```gcloud -v```

Check NPM version

```npm -v```

Create a Node.js app with wizard.

```npm init```

Create and edit your function file.

```touch index.js```

Add a simple function 

```
exports.helloWorld = (req, res) => {
	res.send('Hello World!');
};
```

Install and run in emulator 

```

npm install -g @google-cloud/functions-emulator
functions -v

functions start

functions deploy helloWorld --trigger-http
 
curl http://localhost:8010/gdgdevfesthyd2018/us-central1/helloWorld
 
```

Deploy and run in cloud 

```
gcloud functions deploy helloWorld --runtime nodejs6 --trigger-http

curl https://us-central1-jdalabs-retail-me-dev01.cloudfunctions.net/helloWorld

```

Debug in emulator 
```
functions inspect  helloWorld
```
Connect VS Code to debugger 
Add run configuration 
```

   "configurations": [
    {
      "type": "node",
      "request": "attach",
      "name": "Debug function emulator ",
      "port": 9229
    },
    
```
Add a breakpoint and call the function locally  
```
functions call helloWorld
```
Debug in Chrome Dev tools
``` 
functions inspect  helloWorld
```
Add source 

Add debug point 

```
functions call helloWorld
``` 
Get out of debug mode but keep the sebug settings 
```
functions reset helloWorld --keep
 ```
List and describe the functions deployed in the cloud  
```
gcloud functions list

gcloud functions describe helloWorld
```
Debug in cloud 
```
npm install --save @google-cloud/debug-agent
```
Enable debug
```
require('@google-cloud/debug-agent').start();
```
Redeploy in cloud 
```
 gcloud functions deploy helloWorld --runtime nodejs6 --trigger-http --entry-point helloWorld --project gdgdevfest2018-218215
```

Head over to stackdriver debugger and add source. Click on a line of code to get a snapshot 

Add log points 




