---
layout: post
title:  "Creating a basic Nodejs API project with typescript"
date:   2019-02-09
author: Mahesh Kumar Kolla
categories: NodeJs-project-setup
tags:	Tech NodeJs Typescript
step: "STEP-1" 
prevPost: production-grade-nodejs-api-project-setup
nextPost: creating-basic-nodejs-api-project-with-typescript
published: false
---

{% include nodejs-project-setup-intro.html %}

In this tutorial, We are going to setup a basic express app with typescript.

* Run `npm init` in the project directory and follow the instructions - package.json file would be created.

package.json file contains metadata, dependencies and scripts of the project.
* Install express using `npm install express --save` command

When we specify `--save`, the dependency will be saved in package.json
* Install typescript using `npm install typescript @types/node --save-dev` command

When we specify `--save-dev`, the dependency will be saved under dev dependencies which are required only for development purpose.
* Configuring the typescript. 

When running the typescript `tsc` command, it searches for configuration file `tsconfig.json`. Add the following

{% highlight json %} 
  {
    "compilerOptions": {
      "module": "commonjs",
      "moduleResolution": "node",
      "pretty": true,
      "sourceMap": true,
      "target": "es6",
      "outDir": "./dist"
    },
    "include": [
      "src/**/*.ts"
    ]
  }
{% endhighlight %}

Here, We are specifying various option like source, target, module etc., Read [tsconfig.json][tsconfig] to know about these option.

Now, it is time for us to create the express server

* Create `app.ts` and `server.ts` files under `src` directory

{% highlight typescript %} 
  // app.ts
  import * as express from "express";
  import * as bodyParser from "body-parser";
  const app = express();
  app.use(bodyParser.json());
  app.get('/hello', (req, res) => {
      res.send("Hello");
  });
  export default app;
{% endhighlight %}

Above, we have done two things.
One, We have created an get end point that responds with "Hello". Second, We have used `body-parser` middleware which extracts the body of the request stream and exposes it as json on `req.body`. 

{% highlight typescript %} 
  // server.ts
  import app from "./app";
  const PORT = process.env.PORT || 3000;
  app.listen(PORT, () => {
      console.log(`Express server listening on port ${PORT}`);
  });
{% endhighlight %}

We have created the server and specified a port to listen on.

* Add scripts to package.json.

Add following two lines under scripts in package.json.

{% highlight typescript %}
  "build": "tsc",
  "start": "node ./dist/server.js", 
{% endhighlight %}

This will allow us to build and run the app.

* Run `npm run build` and then `npm start`
* Check the app in browser using URL `localhost:3000/hello`

We need to build and start the server on evey small change of the code. It's kinda takes off focus on development. So, let us create some tools to make this process easy

* Run `npm install nodemon ts-node --save-dev` 

Nodemon helps us to restart the app automatically when any changes detected in the code.
ts-node is for executing the typescript code without compiling it to javascript.

* Add one more script to package.json. `"dev": "nodemon --exec 'ts-node' ./src/server.ts"`

Now, we can run `npm run dev` to start the server in development environment instead of building and running.

We have a basic nodejs app up and running.
In the next tutorial, We will be structuring the app by creating controllers, services, models etc., 


[tsconfig]: https://www.typescriptlang.org/docs/handbook/tsconfig-json.html
