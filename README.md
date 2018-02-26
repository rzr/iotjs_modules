# IoT.js extensions modules #


## DISCLAIMER: ##

* This is work in progress
* repo subject to relocated (please don't fork it until this dislaimer is removed)
* Feedback welcome at:
  - https://github.com/Samsung/iotjs/issues/1441


## DESCRIPTION: ##

This project aims to collect third party additions to be used by IoT.js ( http://iotjs.net ).
IoT.js is an Internet of Things platform using JavaScript and powered by JerryScript engine.

Developers are encouraged to submit changes to upstream project IoT.js first
( https://github.com/samsung/iotjs ), especially if it touches the core framework,
community feedback is always good to listen.

Whatever the contribution is, it could be out of scope of project current focus,
so you can still publish in this side repository for IoT.js's users base.

The main purpose of this "central community repository"
is to provide a set of libraries, tools, drivers, or demo projects to get inspiration from.

Currently IoT.js does not provide a package manager (like Node's NPM),
so it's developer duty to manually pull desired supported modules from iotjs_modules (or all repo).
It's preferred to store modules in an "iotjs_modules" subfolder (like node uses "node_modules").

Here, git modules are used to avoid raw duplication of libs in client projects,
then code is tracked, history preserved and integrity is guaranteed by git.

Note, environment variables can also be helpful
to share modules among projects at user or system's level.

Although full package management and dynamic module loading is not fully available at the moment,
it's encouraged to align to NodeJS/NPM as much as possible.


## USAGE: ##

Extra functionalities beeing added to/for IoT.js should be added as standalone gitmodules.

Each "module" should at least contain:

* "LICENSE*" : It should allows source distribution (as git modules) in "iotjs_modules"
* "package.json" metadata. ("npm init" can be used to generate file https://docs.npmjs.com/cli/init )

Then module's maintainer can share it to iotjs_modules using git (and then submit pull request):

```
cd iotjs_modules
git submodule add https://github.com/{org}/{project}
git commit -sam '{module}: Import to iotjs_modules'
```

If feature requires IoT.js to be changed and rebuilt,
then please explain how and ship patches for iotjs in module's repo, for example:
* mymodule/patches/iotjs/README.md
* mymodule/patches/iotjs/{branch?}/series (to list order of patch files)
* mymodule/patches/iotjs/{branch?}/*.patch


Also make sure to track the origin of patches,
and license them in terms compatible with IoT.js's Apache-2.0.

Piratically, this can be done by adding "meta data" to IoT.js' patches
(or in commit message if using git-format-patch), for example:

```
SPDX-License-Identifier: Apache-2.0
Origin: https://github.com/{org}/iotjs/commit/{CommitId}.patch
IoT.js-DCO-1.0-Signed-off-by: {Author} {Name} {email@host.tld}
```

For other parts then any SPDX approved license ( https://spdx.org/licenses/ )
should be acceptable.


To update submodule, the procedure is straightforward:

```
cd iotjs_modules/{submodule}
git pull origin {branch}
```

Application developers can use git or npm to add a module,
if module is compatible with node (same dependencies), then it can be pulled from npm repo:


```
ls package.json || npm init
npm install {package}
```

If package hosted on npmjs.com is not explictly supported by iotjs,
then it should be forked (package.json updated) and then installed from alternative place ie:

```
npm install https://github.com/{user}/{package}
```

(you can align to URLs and versions listed in iotjs_modules)


Don't hesitate to reach community ( irc://irc.freenode.net/#iotjs ) for help or suggestions.
