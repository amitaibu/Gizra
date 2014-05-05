---
published: false
---

RESTful module is a new approach to providing a REST server in Drupal. Its concepts and philoshopy apepars in the module's README so I won't repeat it, but I'd like to go over some of the points and show examples.
In the past year almost every site we have is either completely decoupled from the server side where AngularJs serves the webapp, or AngularJS plays a smaller part, and we just embed web components inside a Drupal page, to provide a slick UI.

Up until now our goto module was RestWs by the wonderfull Klausi, which wrapps around Entity API module's entity metadata wrapper. Basically, it hands over to the metadata wrapper the resposbility for the access and for the actual value it spits out.
It works fine, however the JSON it exposes has too much information. RestWs allows us to alter the JSON, though.

But then we saw the other problems. Drupalism. As the client you should know that an article is a node entity, and that tags are taxonomy terms. And all the fields are prefied with ``field_``. And on top of that, once we exposed an entity (e.g. node) - all the bundles would be exposed by default.

After trying to impose Gizra's requirements to RestWs and Services Entity, we've realized that the concepts where different enough to start a new module - learning a lot from the other modules. The goal if this module is to allow us to expose a versionable API which is as good as Github, or Flickr, or any other proper REST service (just imaging if Github would force you to enter the bundle of a node, or exposed the repository name under ``field_repository``).

Another important aspect of RESTful is that it does _not_ try to be a pure REST server. No. We're not writing a thesis, we are writing a web application, so we prefer to follow [best practices](http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api) rather then reaching "restful glory".

## Example module

Following our standard of bundling the module with an example module, you can enable the ``RESTful example`` module, and create a few article nodes.
Then visit ``/api/v1/articles`` to see a list of articles, or ``/api/v1/articles/1`` to view article with ID 1.
The code that is responsible for this restful ``resource`` is a CTools plugin, and should be pretty easy for developers to setup.




