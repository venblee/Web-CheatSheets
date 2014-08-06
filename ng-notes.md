
Best practices
==============

$watch/$digest/$apply
---------------------

**refs**
- http://www.benlesh.com/2013/08/angularjs-watch-digest-and-apply-oh-my.html


**$watch**
- DO : in directives to update the DOM when a $scope value changes.
- DON'T : in controllers, it's unnecessary in almost every case. Use a method on the scope to update the value(s) the watch was changing instead.

**$digest/$apply**
- DO : in directives to let Angular know you've made changes after an asynchronous call, such as a DOM event.
- DO : in services to let Angular know some asynchronous operation has returned, such as a WebSocket update (SignalR) or an event from a 3rd party library like Facebook API.
- DON'T : in controllers. Asynchronous operations outside of the Angular framework don't belong in your controllers. They belong in services and directives.


Provier/Service/Factory
-----------------------

**refs**
- http://www.mikeobrien.net/blog/angular-consts-values-services-factories-and-providers-oh-my/
