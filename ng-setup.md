SETUP
=====

ref:
- http://www.toptal.com/angular-js/your-first-angularjs-app-part-2-scaffolding-building-and-testing

rem:
- if issue use cygwin instead of cmd.exe


NPM
---

Basics
-g : install global
--save-dev (save as dev dependency)

Configure npm

```
npm cache clear
npm set strict-ssl false
npm config set registry http://registry.npmjs.org/
npm config set cache C:\tmp\npm_cache --global
npm config set tmp C:\tmp --global
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

GIT
---

Git is required by bower to install/update package

If standard "git:" is blocked, following change it to an https access 
```
git config --global url."https://".insteadOf git://
```


BOWER
-----



.bowerrc (project/.bowerrc)

```
{
  "directory": "bower_components",
  "strict-ssl": false
}
```

manage dependencies

```
install <dependency> --save-dev : save as dev dependency
install <dependency> --save : save as production dependency
```




TEST (KARMA)
------------
Install

```
npm install karma-jasmine --save-dev
npm install karma-cli --save-dev
npm install karma-chrome-launcher --save-dev
npm install karma-coverage  --save-dev
```

Configure

karma.conf.js (project/test/karma.conf.js)

```

    frameworks: ['jasmine'],
    
    plugins: [
      'karma-chrome-launcher',
      'karma-jasmine'
    ],


    browsers: [
      'Chrome'
    ],

```




```
- http://www.ng-newsletter.com/advent2013/#!/day/19
- https://www.artandlogic.com/blog/2013/05/angularjs-best-practices-ive-been-doing-it-wrong-part-1-of-3/


-> Install global, add Karma to PATH

LIB/DEPENDENCIES SETUP (VIA BOWER)


```
bower install angular-ui-router --save-dev
bower install angular-bootstrap --save-dev

```
