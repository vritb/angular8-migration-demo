# Migration Log
This log will document the steps taken to migrate an existing Angular8 demo application to Angular Version ^15.0.0.

The original demo needs an JWT authenication server. This server is provided as a java project at [https://github.com/only2dhir/spring-boot-jwt].

I will perforn a brute force migration i.e. get the original application running but don't change the existing directory layout, architecture or code unless I am forced to.

## Software Packages Used In Original Demo Application
| Software | Version | 
| :---: | :---: |
| Angular | 8.0.3 |
| Typescript | 3.4.3 |
| rxjs | 6.4.0 | 
| tslib | 1.9.0 |
| zone.js | 0.9.1 |

## Preparations
1. Fork the original demo app on github
2. run `npm install`
There will be lots of warnings.
```text
npm WARN old lockfile 
npm WARN old lockfile The package-lock.json file was created with an old version of npm,
npm WARN old lockfile so supplemental metadata must be fetched from the registry.
npm WARN old lockfile 
npm WARN old lockfile This is a one-time fix-up, please be patient...
npm WARN old lockfile 
npm WARN deprecated fsevents@1.2.9: fsevents 1 will break on node v14+ and could be using insecure binaries. Upgrade to fsevents 2.
npm WARN deprecated ini@1.3.5: Please update to ini >=1.3.6 to avoid a prototype pollution issue
npm WARN deprecated har-validator@5.1.3: this library is no longer supported
npm WARN deprecated debug@3.2.6: Debug versions >=3.2.0 <3.2.7 || >=4 <4.3.1 have a low-severity ReDos regression when used in a Node.js environment. It is recommended you upgrade to 3.2.7 or 4.3.1. (https://github.com/visionmedia/debug/issues/797)
npm WARN deprecated debug@3.2.6: Debug versions >=3.2.0 <3.2.7 || >=4 <4.3.1 have a low-severity ReDos regression when used in a Node.js environment. It is recommended you upgrade to 3.2.7 or 4.3.1. (https://github.com/visionmedia/debug/issues/797)
npm WARN deprecated debug@3.2.6: Debug versions >=3.2.0 <3.2.7 || >=4 <4.3.1 have a low-severity ReDos regression when used in a Node.js environment. It is recommended you upgrade to 3.2.7 or 4.3.1. (https://github.com/visionmedia/debug/issues/797)
npm WARN deprecated debug@3.2.6: Debug versions >=3.2.0 <3.2.7 || >=4 <4.3.1 have a low-severity ReDos regression when used in a Node.js environment. It is recommended you upgrade to 3.2.7 or 4.3.1. (https://github.com/visionmedia/debug/issues/797)
npm WARN deprecated debug@3.2.6: Debug versions >=3.2.0 <3.2.7 || >=4 <4.3.1 have a low-severity ReDos regression when used in a Node.js environment. It is recommended you upgrade to 3.2.7 or 4.3.1. (https://github.com/visionmedia/debug/issues/797)
npm WARN deprecated debug@4.1.1: Debug versions >=3.2.0 <3.2.7 || >=4 <4.3.1 have a low-severity ReDos regression when used in a Node.js environment. It is recommended you upgrade to 3.2.7 or 4.3.1. (https://github.com/visionmedia/debug/issues/797)
npm WARN deprecated debug@4.1.1: Debug versions >=3.2.0 <3.2.7 || >=4 <4.3.1 have a low-severity ReDos regression when used in a Node.js environment. It is recommended you upgrade to 3.2.7 or 4.3.1. (https://github.com/visionmedia/debug/issues/797)
npm WARN deprecated debug@4.1.1: Debug versions >=3.2.0 <3.2.7 || >=4 <4.3.1 have a low-severity ReDos regression when used in a Node.js environment. It is recommended you upgrade to 3.2.7 or 4.3.1. (https://github.com/visionmedia/debug/issues/797)
npm WARN deprecated debug@4.1.1: Debug versions >=3.2.0 <3.2.7 || >=4 <4.3.1 have a low-severity ReDos regression when used in a Node.js environment. It is recommended you upgrade to 3.2.7 or 4.3.1. (https://github.com/visionmedia/debug/issues/797)
npm WARN deprecated debug@4.1.1: Debug versions >=3.2.0 <3.2.7 || >=4 <4.3.1 have a low-severity ReDos regression when used in a Node.js environment. It is recommended you upgrade to 3.2.7 or 4.3.1. (https://github.com/visionmedia/debug/issues/797)
npm WARN deprecated debug@4.1.1: Debug versions >=3.2.0 <3.2.7 || >=4 <4.3.1 have a low-severity ReDos regression when used in a Node.js environment. It is recommended you upgrade to 3.2.7 or 4.3.1. (https://github.com/visionmedia/debug/issues/797)
npm WARN deprecated debug@4.1.1: Debug versions >=3.2.0 <3.2.7 || >=4 <4.3.1 have a low-severity ReDos regression when used in a Node.js environment. It is recommended you upgrade to 3.2.7 or 4.3.1. (https://github.com/visionmedia/debug/issues/797)
npm WARN deprecated sourcemap-codec@1.4.4: Please use @jridgewell/sourcemap-codec instead
npm WARN deprecated uuid@3.3.2: Please upgrade  to version 7 or higher.  Older versions may use Math.random() in certain circumstances, which is known to be problematic.  See https://v8.dev/blog/math-random for details.
npm WARN deprecated source-map-resolve@0.5.2: See https://github.com/lydell/source-map-resolve#deprecated
npm WARN deprecated streamroller@1.0.5: 1.x is no longer supported. Please upgrade to 3.x or higher.
npm WARN deprecated read-package-tree@5.2.2: The functionality that this package provided is now in @npmcli/arborist
npm WARN deprecated readdir-scoped-modules@1.1.0: This functionality has been moved to @npmcli/fs
npm WARN deprecated request@2.88.0: request has been deprecated, see https://github.com/request/request/issues/3142
npm WARN deprecated log4js@4.4.0: 4.x is no longer supported. Please upgrade to 6.x or higher.
npm WARN deprecated node-fetch-npm@2.0.2: This module is not used anymore, npm uses minipass-fetch for its fetch implementation now
npm WARN deprecated protractor@5.4.2: We have news to share - Protractor is deprecated and will reach end-of-life by Summer 2023. To learn more and find out about other options please refer to this post on the Angular blog. Thank you for using and contributing to Protractor. https://goo.gle/state-of-e2e-in-angular
npm WARN deprecated date-format@2.0.0: 2.x is no longer supported. Please upgrade to 4.x or higher.
npm WARN deprecated chokidar@2.1.6: Chokidar 2 does not receive security updates since 2019. Upgrade to chokidar 3 with 15x fewer dependencies
npm WARN deprecated buffer@4.9.1: This version of 'buffer' is out-of-date. You must update to v4.9.2 or newer
npm WARN deprecated acorn-dynamic-import@4.0.0: This is probably built in to whatever tool you're using. If you still need it... idk
npm WARN deprecated @schematics/update@0.800.6: This was an internal-only Angular package up through Angular v11 which is no longer used or maintained. Upgrade Angular to v12+ to remove this dependency.
npm WARN deprecated core-js@3.0.1: core-js@<3.23.3 is no longer maintained and not recommended for usage due to the number of issues. Because of the V8 engine whims, feature detection in old core-js versions could cause a slowdown up to 100x even if nothing is polyfilled. Some versions have web compatibility issues. Please, upgrade your dependencies to the actual version of core-js.
npm WARN deprecated urix@0.1.0: Please see https://github.com/lydell/urix#deprecated
npm WARN deprecated source-map-url@0.4.0: See https://github.com/lydell/source-map-url#deprecated
npm WARN deprecated resolve-url@0.2.1: https://github.com/lydell/resolve-url#deprecated
npm WARN deprecated querystring@0.2.0: The querystring API is considered Legacy. new code should use the URLSearchParams API instead.
npm WARN deprecated core-js@2.6.9: core-js@<3.23.3 is no longer maintained and not recommended for usage due to the number of issues. Because of the V8 engine whims, feature detection in old core-js versions could cause a slowdown up to 100x even if nothing is polyfilled. Some versions have web compatibility issues. Please, upgrade your dependencies to the actual version of core-js.
npm WARN deprecated mkdirp@0.5.1: Legacy versions of mkdirp are no longer supported. Please update to mkdirp 1.x. (Note that the API surface has changed to use Promises in 1.x.)
npm WARN deprecated core-js@2.6.9: core-js@<3.23.3 is no longer maintained and not recommended for usage due to the number of issues. Because of the V8 engine whims, feature detection in old core-js versions could cause a slowdown up to 100x even if nothing is polyfilled. Some versions have web compatibility issues. Please, upgrade your dependencies to the actual version of core-js.

added 1013 packages, and audited 1014 packages in 28s

91 vulnerabilities (2 low, 29 moderate, 42 high, 18 critical)

To address issues that do not require attention, run:
  npm audit fix

To address all issues (including breaking changes), run:
  npm audit fix --force

Run `npm audit` for details.
```
3. Use Latest LTS Node
Using `nvm` Node Version Manager to select the matching LTS version of NodeJS for Angular 15.
If you don't have `nvm` install visit [https://gist.github.com/d2s/372b5943bce17b964a79].

Then use `nvm` to select the latest LTS build of NodeJS.

```zsh
nvm use --lts
```
4. 