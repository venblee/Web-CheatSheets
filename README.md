NG-CheatSheet
=====================
ref:
- http://www.toptal.com/angular-js/your-first-angularjs-app-part-2-scaffolding-building-and-testing

rem:
- if issue use cygwin instead of cmd.exe

SETUP
=====

NPM
---
```
npm cache clear
npm set strict-ssl false
npm config set registry http://registry.npmjs.org/
npm config set cache C:\Tmp\npm_cache --global
npm config set tmp C:\Tmp --global

```

GRUNT/BOWER/YEOMAN
------------------

Install grunt bower and yeoman global (recommended)

```
npm install -g yo grunt-cli bower 
npm install -g generator-angular
```

Install grunt bower and yeoman local (if global doesn't work out)
```
npm install yo grunt-cli bower --save-dev
npm install generator-angular
```

YEOMAN
------

Install global grunt bower and yeoman

```
npm install -g yo grunt-cli bower 
npm install yo grunt-cli bower  --save-dev



```

TESTS
-----
- http://www.ng-newsletter.com/advent2013/#!/day/19
- https://www.artandlogic.com/blog/2013/05/angularjs-best-practices-ive-been-doing-it-wrong-part-1-of-3/

```
npm install karma-jasmine@2_0 --save-dev
npm install karma-cli --save-dev
npm install karma-chrome-launcher --save-dev
npm install karma-coverage  --save-dev
npm install karma-chrome-launcher --save-dev
```

-> Install global, add Karma to PATH

