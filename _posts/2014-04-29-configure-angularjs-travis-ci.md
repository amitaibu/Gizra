---
title: Configure AngularJS apps in Travis CI
tags:
  - angularjs
  - angular
  - javascript
  - test
  - travis-ci
  - examples
permalink: "/content/configure-angularjs-"
layout: post
author: CarlosMantilla
---
{% include JB/setup %}

If your plan is create a new open source project or contribute in a popular project.

Continuous integration Tools like [Travis CI](https://travis-ci.org/) are fundamentals, to have a nice trip! to continous deployment.

We can implement this very fast in an [AngularJS](https://angularjs.org/) application using yeoman.io, and the powerful [AngularJS generator](https://github.com/yeoman/generator-angular), this create test files and configuration files for the tools like travis, karma and grunt.

<!-- more -->

Here you can find an [example](https://github.com/ceoaliongroo/contrib/tree/master/angular-travis) to accelerate the configuration process and you can go directly to create the logic of your application.

Let's configure together travis ci for the AngularJS application genereted by yeoman.io:

- Open karma.conf.js and change to Firefox travis ci do not support chrome configure by default.

```javascript
  browsers: ['Firefox'],
```

- Add travis ci configuration to run karma unit test files:

- Configure webhook in github.

- Check the test runnig in travis ci.

Extra points: There are good articles and videos that explain, all the importance and the process of mantain continous integration in your angularjs project.


