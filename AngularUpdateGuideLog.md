
Command

```zsh
➜  angular8-migration-demo git:(Angular-Update-Guide) ✗ node --version
v19.4.0
➜  angular8-migration-demo git:(Angular-Update-Guide) ✗ nvm use --lts
Now using node v18.13.0 (npm v8.19.3)
➜  angular8-migration-demo git:(Angular-Update-Guide) ✗ NG_DISABLE_VERSION_CHECK=1 npx @angular/cli@8 update @angular/core@8 @angular/cli@8 
```
Console Output
```zsh
Using package manager: 'npm'
Collecting installed dependencies...
Found 30 dependencies.
Fetching dependency metadata from registry...
    Updating package.json with dependency @angular/cli @ "8.3.29" (was "8.0.6")...
    Updating package.json with dependency @angular/core @ "8.2.14" (was "8.0.3")...
    Updating package.json with dependency @angular/platform-browser @ "8.2.14" (was "8.0.3")...
    Updating package.json with dependency rxjs @ "6.6.7" (was "6.4.0")...
    Updating package.json with dependency @angular-devkit/build-angular @ "0.803.29" (was "0.800.6")...
    Updating package.json with dependency @angular/common @ "8.2.14" (was "8.0.3")...
    Updating package.json with dependency typescript @ "3.5.3" (was "3.4.5")...
    Updating package.json with dependency @angular/forms @ "8.2.14" (was "8.0.3")...
    Updating package.json with dependency @angular/animations @ "8.2.14" (was "8.0.3")...
    Updating package.json with dependency @angular/platform-browser-dynamic @ "8.2.14" (was "8.0.3")...
    Updating package.json with dependency @angular/router @ "8.2.14" (was "8.0.3")...
    Updating package.json with dependency @angular/compiler @ "8.2.14" (was "8.0.3")...
    Updating package.json with dependency @angular/compiler-cli @ "8.2.14" (was "8.0.3")...
    Updating package.json with dependency @angular/language-service @ "8.2.14" (was "8.0.3")...
UPDATE package.json (1307 bytes)
npm WARN deprecated fsevents@1.2.9: fsevents 1 will break on node v14+ and could be using insecure binaries. Upgrade to fsevents 2.
npm WARN deprecated @npmcli/move-file@1.1.2: This functionality has been moved to @npmcli/fs
npm WARN deprecated chokidar@2.1.8: Chokidar 2 does not receive security updates since 2019. Upgrade to chokidar 3 with 15x fewer dependencies
npm WARN deprecated node-fetch-npm@2.0.4: This module is not used anymore, npm uses minipass-fetch for its fetch implementation now
npm WARN deprecated uuid@3.4.0: Please upgrade  to version 7 or higher.  Older versions may use Math.random() in certain circumstances, which is known to be problematic.  See https://v8.dev/blog/math-random for details.
npm WARN deprecated @schematics/update@0.803.29: This was an internal-only Angular package up through Angular v11 which is no longer used or maintained. Upgrade Angular to v12+ to remove this dependency.
npm WARN deprecated read-package-tree@5.3.1: The functionality that this package provided is now in @npmcli/arborist
npm WARN deprecated core-js@3.6.4: core-js@<3.23.3 is no longer maintained and not recommended for usage due to the number of issues. Because of the V8 engine whims, feature detection in old core-js versions could cause a slowdown up to 100x even if nothing is polyfilled. Some versions have web compatibility issues. Please, upgrade your dependencies to the actual version of core-js.

added 331 packages, removed 62 packages, changed 274 packages, and audited 1283 packages in 49s

78 packages are looking for funding
  run `npm fund` for details

62 vulnerabilities (2 low, 16 moderate, 29 high, 15 critical)

To address issues that do not require attention, run:
  npm audit fix

To address all issues (including breaking changes), run:
  npm audit fix --force

Run `npm audit` for details.
```
