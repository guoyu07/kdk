## Setup your environment

### Prerequisites

#### Install Node.js

[Node](https://nodejs.org/en/) is a server platform which runs JavaScript.
It's lightweight and efficient.
It has the largest ecosystem of open source libraries in the world.

- [Default install.](https://nodejs.org/en/)
- [Specific versions.](https://nodejs.org/en/download/)

> **Kalisio modules are expected to work with Node.js >= 8**

**In order to be able to switch easily between different versions of Node.js we recommand to use a version manager like [n](https://github.com/tj/n)/[nvm](https://github.com/creationix/nvm) under Linux/Mac or [nvm](https://github.com/coreybutler/nvm-windows) under Windows.**

#### Install Git

[git](https://git-scm.com/) is the version control system most frequently used in open source.
There are many resources available for installing it.

- [Linux.](https://www.atlassian.com/git/tutorials/install-git#linux)
- [macOS.](https://www.atlassian.com/git/tutorials/install-git#mac-os-x)
- [Windows.](https://www.atlassian.com/git/tutorials/install-git#windows)

#### Install MongoDB

[Mongo](https://www.mongodb.com/) is an open-source, document database designed for ease of development and scaling.

- [Linux.](https://docs.mongodb.com/manual/administration/install-on-linux/)
- [macOS.](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/)
- [Windows.](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/)

> **Kalisio modules are expected to work with MongoDB >= 3**

#### Install Yarn

Due to some [changes](http://codetunnel.io/npm-5-changes-to-npm-link/) in the way `npm` manages linked modules we prefer to use [Yarn](https://yarnpkg.com) as a package manager.

[Install Yarn](https://yarnpkg.com/en/docs/install) on your platform.

https://yarnpkg.com

#### Install Quasar CLI

Install the Quasar CLI : `$ npm install -g quasar-cli`

#### Install Cordova ecosystem

Follow this [tutorial](https://evothings.com/doc/build/cordova-install-windows.html).

### Web app

While it is a WIP and not yet pushed to NPM, or when developing, please use the following process.

First clone all the modules/plugins you need and use [yarn/npm link](https://docs.npmjs.com/cli/link) to make them globally available to your Node.js installation:

```bash
// Clone and link the plugins
git clone https://github.com/kalisio/kCore.git
cd kCore
yarn link

git clone https://github.com/kalisio/kTeam.git
cd kTeam
yarn link

git clone https://github.com/kalisio/kClient.git
cd kClient
yarn link

...
```

Then clone the main app repository and link to modules/plugins to make Node.js pointing to the previously cloned modules instead of those installed by yarn/npm, e.g. :
```bash
// Clone and link plugins to Kalisio app
git clone https://github.com/kalisio/kApp.git
cd kApp
// Client side
yarn link kCore
yarn link kTeam
// API side
cd api
yarn link kCore
yarn link kTeam
...
```

> **Take care that a top-level plugin might depend on another plugin so you will have to link them together, for instance the kTeam plugin depends on the kCore plugin.**

### Cordova wrapper

Follow [Quasar guide](http://quasar-framework.org/guide/cordova-wrapper.html).

Under Windows you might have somme issue creating a symbolic link. First you need to have administrator privileges in your shell. Then  the easy way is to use the [PowerShell Community Extensions](http://pscx.codeplex.com/) and the `New-SymLink dir link_target` command. The environment variable `PSModulePath` needs to be updated to add the path to the extension (eg `C:\Program Files (x86)\PowerShell Community Extensions\Pscx3\Pscx`) and the command should be run as administrator or your user should have [appropriate rights](http://superuser.com/questions/104845/permission-to-make-symbolic-links-in-windows-7).

If you have some issue about *You have not accepted the license agreements of the following SDK components...* you need to update first your installed SDKs through *Android Studio > Configure > SDK Manager > Install*. You might need to do it multiple times since the last version of a SDK only appear for download when previous version dependencies are installed.

To have a viable emulator install [HAXM](https://software.intel.com/en-us/articles/intel-hardware-accelerated-execution-manager-intel-haxm).
