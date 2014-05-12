---
title: Configure AngularJS apps in Travis CI
tags:
  - yeoman.io
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

A great programmer, not only need great tools and skills when work in a new open source project or contribute to a popular one.

In this road to the next release of the application always have many obstacles and detours (improvisation and losing focus of the specifications application), best practices could save us for that kind of issues, hereby continuous integration tools like [Travis CI](https://travis-ci.org/) are fundamentals, to have a nice trip! to continuous deployment.

We can implement this very fast in an [AngularJS](https://angularjs.org/) application using [yeoman.io](http://yeoman.io/), and the powerful [AngularJS generator](https://github.com/yeoman/generator-angular), this create test files structure and configuration files to test with karma, grunt anf travis.

<!-- more -->

Here you can find an [example](https://github.com/ceoaliongroo/angular-travis-config-example) code.

Let's configure together travis ci for the AngularJS application genereted by [yeoman.io](http://yeoman.io/):

# Create the application and configure.

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
#Prerequisite: Firefox browser 17+ installed locally for 'grunt test' locally.

- Install karma and dependencies to test in travis with firefox.

```bash
$ npm install karma grunt-karma karma-jasmine karma-firefox-launcher --save-dev
```

- Modify travis ci configuration file to run karma unit test files, you can open .travis.yml
#Have to be in the root folder of the github repository.):

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
# Configure Github Webhook and Test.

- Click the icon Settings

![]({{BASE_PATH}}/assets/images/posts/configure-angularjs-travis-ci/settings.png)

- Select Webhooks & Services, click the button Add service, search for travis ci

![]({{BASE_PATH}}/assets/images/posts/configure-angularjs-travis-ci/webhooks.png)

- Configure github webhook for travis ci to automatic test each commit.

![]({{BASE_PATH}}/assets/images/posts/configure-angularjs-travis-ci/configure.png)

- Push some code and check the test is runnig on travis ci site.

![]({{BASE_PATH}}/assets/images/posts/configure-angularjs-travis-ci/testing.png)

Now every commit you will be inform if some commit broke the application.


