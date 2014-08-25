QUICK SETUP (FROM AN EXISTING PROJECT)
======================================
- (PATH - > System Properties -> Enviromental Variables -> User Variables ) 
- Install node (including npm) + npm to PATH
- Install git + git.exe to PATH

-- Running the Following Setup  in CMD 
- npm
```
npm cache clear
npm set strict-ssl false
npm config set registry http://registry.npmjs.org/
npm config set cache C:\tmp\npm_cache --global
npm config set tmp C:\tmp --global
```
- Restart CMD 
- git
```
git config --global url."https://".insteadOf git://
```

-- Running the Following Setup from the Root of the Project in CMD 
- retrieve npm packages 
```
npm install
```

- retrieve bower dependencies
```
bower install
```

- run the project
```
grunt serve --force
```

SETUP
=====

ref:
- http://www.toptal.com/angular-js/your-first-angularjs-app-part-2-scaffolding-building-and-testing

rem:
- if issue use cygwin instead of cmd.exe


NODE
----

Installation
- http://nodejs.org/ 
- Add exe to PATH


NPM
---

***Install***
- Included within node


***Note***
```
-g : install global
--save-dev (save as dev dependency)
```

***Config***
```
npm cache clear
npm set strict-ssl false
npm config set registry http://registry.npmjs.org/
npm config set cache C:\tmp\npm_cache --global
npm config set tmp C:\tmp --global
```

GIT
---

***Install***
- https://windows.github.com/
- Add exe to PATH

***Config***
If standard "git://" is blocked, following change it to an https access 
```
git config --global url."https://".insteadOf git://
```

GRUNT/BOWER/YEOMAN
------------------

***Install global***  

Will install node package in the common shared folder (recommended)

```
npm install -g yo grunt-cli bower 
npm install -g generator-angular
```

***Install local***

Will put package specifically in the porject location

```
npm install yo grunt-cli bower --save-dev
npm install generator-angular
```


BOWER
-----

***Config***

.bowerrc (project/.bowerrc)

```
{
  "directory": "bower_components",
  "strict-ssl": false
}
```

***Usage***

manage dependencies

```
install <dependency> --save-dev : save as dev dependency
install <dependency> --save : save as production dependency
```

SASS
----

You need to install Ruby first, so download and install it from here: 
http://dl.bintray.com/oneclick/rubyinstaller/ruby-1.9.3-p545-i386-mingw32.7z?direct


Then in order to make compass work properly:
```
gem update --system
gem sources –r https://rubygems.org/
gem sources –c
gem sources –a http://rubygems.org
gem install compass
```

TEST (KARMA)
------------
***Install***

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

-> Install global, add Karma to PATH

LIB/DEPENDENCIES SETUP (VIA BOWER)
----------------------------------

```
bower install angular-ui-router --save
bower install angular-bootstrap --save
```
