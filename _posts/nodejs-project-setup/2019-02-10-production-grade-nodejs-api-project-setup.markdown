---
layout: post
title:  "Production-grade Nodejs API project setup"
date:   2019-02-10
author: Mahesh Kumar Kolla
categories: nodejs-project-setup
tags:	tech javascript nodejs
---
These are series of tutorials that help to setup production-grade Nodejs API project that follows SOLID principles. 

Javascript has been powering the web from a long time. Nodejs has taken javascript to another level to use it in server side development.
Many people are moving to Nodejs because of its performance. 
In my opinion, the actual computations performance is similar to any other language like java. 
But what makes Nodejs better is it's non-blocking io operations. This makes Nodejs perform well in web applications where the handling requests are challenging.    

But it is still a challenge to write scalable applications in pure Nodejs. The following frameworks can help us build scalable applications.

* [Express JS][expressjs]{:target="_blank"} - Web application framework.
Express helps us organise and makes it easier to write web applications in js.
* [Typescript][typescript]{:target="_blank"} - A typed superset of javascript.
This helps us to catch the bugs well ahead and before they go into production.
* [Jest][jest]{:target="_blank"} - Testing framework.
Jest is simple and fast. It has out of the box features like mocking, code coverage, expectation/assertions etc., 
* [InversifyJS][inversifyjs]{:target="_blank"} - IoC container.
Dependency Inject is one of the SOLID principles. InversifyJs is one of the great and lightweight IoC containers for typescript.  

#### STEP-1: [Creating a basic Nodejs API project with typescript](creating-basic-nodejs-api-project-with-typescript)
#### STEP-2: Structuring the Nodejs API project - COMING SOON
#### STEP-3: Setup database and migrations to NodeJs project - COMING SOON
#### STEP-4: Setup Logging, Linting and Dependency checker to NodeJs Project - COMING SOON
#### STEP-4: Test setup for NodeJs project - COMING SOON
#### STEP-6: Dependency injection in NodeJs using InversifyJs - COMING SOON
#### STEP-7: Dockerising the NodeJs App - COMING SOON


[expressjs]: https://expressjs.com/
[typescript]: https://www.typescriptlang.org/
[jest]: https://jestjs.io/
[inversifyjs]: http://inversify.io/
