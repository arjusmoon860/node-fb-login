# Facebook Login
Author : [Arju S Moon](http://codemaster)
[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://codemaster.online)

Facebook login modules, which can be used in your Node, Express.js Applications

  - Get Auth URL
  - Get Facebook Access Token
  - Get long-lived Access Token (Valid for 60 days)
  - Get Facebook User Profile

### Installation

Requires [Node.js](https://nodejs.org/) v12+ to run.

Install the dependencies and devDependencies and start the server.

```sh
$ npm install node-fb-login
```

### Usage

```javascript
const nodeFbLogin = require('node-fb-login');

// Generate authentication URL
nodeFbLogin.generateAuthURL({
  fbAppID: "API_ID",
  redirectURI: "REDIRECT_URI",
  scopes:["public_profile","email"]
}).then(URL=>{
  console.log(URL);
}).catch(error=>{
  console.log(error);
})

// Get the short-lived Access Token by passing the code recieved from the Auth URL
nodeFbLogin.getAccessToken({
  code: "AUTH_CODE",
  fbAppID: "APP_ID",
  fbAppSecret: "APP_SECRET",
  redirectURI: "REDIRECT_URI"
}).then(accessToken => {
  console.log(accessToken);
}).catch(error => {
  console.log(error);
})

// Get the User profile by passing the Access Token
nodeFbLogin.getUserProfile({
  accessToken:"ACCESS_TOKEN",
  fields: ["id","name","email"]
}).then(user => {
  console.log(user);
}).catch(error => {
  console.log(error);
})

// Get long-lived Access Token by passing the short-lived access token (Valid for 60 days)
nodeFbLogin.getLongLivedAccessToken({
  fbAppID: "APP_ID",
  fbAppSecret: "APP_SECRET",
  accessToken: "ACCESS_TOKEN"
}).then(accessToken => {
  console.log(accessToken);
}).catch(error => {
  console.log(error);
})
```
