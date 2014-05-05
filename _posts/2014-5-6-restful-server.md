---
published: false
---

RESTful module is a new approach to providing a REST server in Drupal. Its concepts and philoshopy apepars in the module's README, but I'd like to go over some of the points and show example.
In the past year almost every site we have is either completely decoupled from the server side where AngularJs serves the webapp, or AngularJS plays a smaller part, and we just embed web components inside a Drupal page, to provide a slick UI.

Up until now our goto module was RestWs by the wonderfull Klausi, which wrapps around Entity API module's entity metadata wrapper. Basically, it hands over to the metadata wrapper the resposbility for the access and for the actual value it spits out.
It works fine, however the JSON it exposes has too much information. RestWs allows us to alter the JSON, though.

But then we saw the other problems. Drupalism. As the client you should know that an article is a node entity, and that tags are taxonomy terms. And all the fields are prefied with ``field_``. And on top of that, once we exposed an entity (e.g. node) - all the bundles would be exposed by default.

After trying to impose Gizra's requirements to RestWs and Services Entity, we've realized that the concept where different enough to start a new module.


