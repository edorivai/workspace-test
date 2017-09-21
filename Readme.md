# `Yarn add` bug showcase

Steps I followed:

1. Create an empty directory(`workspace-1`), and add a minimal `package.json` file.
2. In root `package.json`, set `"workspaces": [ "./*" ]`
3. Run:
```
cd workspace-1
yarn add lodash.assign
```
4. By now, I'd have (also see [screenshot](/directory-structure.png))
```
/workspace-1
  /node_modules
    /lodash.assign
```
While I would have expected

```
/node_modules
  /lodash.assign
/workspace-1
```
With node modules being installed at the root level.
5. Now running `yarn` at the root directory installs the `lodash.assign` dependency at the root.


## System info and versions:
```
$ uname -srvo
Linux 4.4.0-93-generic #116-Ubuntu SMP Fri Aug 11 21:17:51 UTC 2017 GNU/Linux

$ lsb_release -rcd
Description:    Ubuntu 16.04.3 LTS
Release:        16.04
Codename:       xenial

$ node --version
v8.5.0

$ npm --version
5.3.0

$ yarn --version
1.0.2-20170921.1145
```