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

We can implement this very fast in an [AngularJS](https://angularjs.org/) application using [yeoman.io](http://yeoman.io/), and the powerful [AngularJS generator](https://github.com/yeoman/generator-angular), this create test files and configuration files for the tools like travis, karma and grunt.

<!-- more -->

Here you can find an [example](https://github.com/ceoaliongroo/contrib/tree/master/angular-travis) to accelerate the configuration process and you can go directly to create the logic of your application.

Let's configure together travis ci for the AngularJS application genereted by yeoman.io:

- Create new angular application

```bash
$ yo angular:app application_name
```

- Open Gruntfile.js and modify the karma configuration:

```javascript
  // Test settings
  karma: {
    unit: {
      configFile: 'karma.conf.js',
      singleRun: true,
      browsers: ['Firefox']
    }
  }
```

Adding the line `browsers: ['Firefox']` permit run the test with firefox, this is compatible with travis ci.

- Open karma.conf.js and change to Firefox travis ci do not support chrome configure by default.

```javascript
  browsers: ['Firefox'],
```

- Install karma and dependencies to test.

```bash
$ npm install karma grunt-karma karma-jasmine karma-firefox-launcher --save-dev
```

- Modify travis ci configuration file to run karma unit test files, you can open travis.yml (normally in the root of the project):

```yaml
  language: node_js
  node_js:
    - '0.10'
  before_install:
    - 'export DISPLAY=:99.0'
    - 'sh -e /etc/init.d/xvfb start'
  before_script:
    - 'gem update --system'
    - 'gem install sass --version "=3.2.12"'
    - 'gem install compass --version "=0.12.2"'
    - 'npm install -g bower grunt-cli karma-cli'
    - 'bower install'
```

- Click the icon Settings

![]({{BASE_PATH}}/assets/images/posts/configure-angularjs-travis-ci/settings.png)

- Select Webhooks & Services, click the button Add service, search for travis ci

![]({{BASE_PATH}}/assets/images/posts/configure-angularjs-travis-ci/webhooks.png)

- Configure github webhook for travis ci to automatic test each commit.

![]({{BASE_PATH}}/assets/images/posts/configure-angularjs-travis-ci/configure.png)


- Push some code and check the test runnig on travis ci site.


Extra points: There are good articles and videos that explain, all the importance and the process of mantain continous integration in your angularjs project.


