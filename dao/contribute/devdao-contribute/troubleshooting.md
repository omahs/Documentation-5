---
description: Dev Environment Setup and commonly reported issues
---

# Troubleshooting

If you run into issues with the dev environment for the Kwenta dApp, please read the troubleshooting information below. If this doesn't help you further, don't hesitate to ask the devDAO community in the `#community-dev` channel for assistance!&#x20;

Please make sure you are on the latest stable (LTS) versions of `nodejs` and `npm`.

### NPM issues with webpack

When introducing new packages or updating packages, users reported errors, similar to these below:

```
platschi@platschi kwenta % npm run dev
[...]
TypeError: Cannot read properties of undefined (reading 'tap')
    at /Users/platschi/Templates/devDAO/leovct/kwenta/node_modules/@next/react-refresh-utils/ReactRefreshWebpackPlugin.js:100:61
    at SyncHook.eval [as call] (eval at create (/Users/platschi/Templates/devDAO/leovct/kwenta/node_modules/tapable/lib/HookCodeFactory.js:19:10), <anonymous>:7:1)
    at SyncHook.lazyCompileHook (/Users/platschi/Templates/devDAO/leovct/kwenta/node_modules/tapable/lib/Hook.js:154:20)
    at Compiler.newCompilation (/Users/platschi/Templates/devDAO/leovct/kwenta/node_modules/next/node_modules/webpack/lib/Compiler.js:631:26)
    at /Users/platschi/Templates/devDAO/leovct/kwenta/node_modules/next/node_modules/webpack/lib/Compiler.js:667:29
    at AsyncSeriesHook.eval [as callAsync] (eval at create (/Users/platschi/Templates/devDAO/leovct/kwenta/node_modules/tapable/lib/HookCodeFactory.js:33:10), <anonymous>:6:1)
    at AsyncSeriesHook.lazyCompileHook (/Users/platschi/Templates/devDAO/leovct/kwenta/node_modules/tapable/lib/Hook.js:154:20)
    at Compiler.compile (/Users/platschi/Templates/devDAO/leovct/kwenta/node_modules/next/node_modules/webpack/lib/Compiler.js:662:28)
    at /Users/platschi/Templates/devDAO/leovct/kwenta/node_modules/next/node_modules/webpack/lib/Watching.js:77:18
    at AsyncSeriesHook.eval [as callAsync] (eval at create (/Users/platschi/Templates/devDAO/leovct/kwenta/node_modules/tapable/lib/HookCodeFactory.js:33:10), <anonymous>:15:1)
```

```
platschi@platschi kwenta % npm i
npm WARN ERESOLVE overriding peer dependency
npm ERR! code ERESOLVE
npm ERR! ERESOLVE could not resolve
npm ERR! 
npm ERR! While resolving: eslint-config-react-app@6.0.0
npm ERR! Found: eslint-plugin-testing-library@5.3.1
npm ERR! node_modules/eslint-plugin-testing-library
npm ERR!   dev eslint-plugin-testing-library@"^5.1.0" from the root project
npm ERR! 
npm ERR! Could not resolve dependency:
npm ERR! peerOptional eslint-plugin-testing-library@"^3.9.0" from eslint-config-react-app@6.0.0
npm ERR! node_modules/eslint-config-react-app
npm ERR!   dev eslint-config-react-app@"6.0.0" from the root project
npm ERR! 
npm ERR! Conflicting peer dependency: eslint-plugin-testing-library@3.10.2
npm ERR! node_modules/eslint-plugin-testing-library
npm ERR!   peerOptional eslint-plugin-testing-library@"^3.9.0" from eslint-config-react-app@6.0.0
npm ERR!   node_modules/eslint-config-react-app
npm ERR!     dev eslint-config-react-app@"6.0.0" from the root project
npm ERR! 
npm ERR! Fix the upstream dependency conflict, or retry
npm ERR! this command with --force, or --legacy-peer-deps
npm ERR! to accept an incorrect (and potentially broken) dependency resolution.
npm ERR! 
npm ERR! See /Users/platschi/.npm/eresolve-report.txt for a full report.

npm ERR! A complete log of this run can be found in:
npm ERR!     /Users/platschi/.npm/_logs/2022-04-20T17_24_43_242Z-debug-0.log
```

One temporary solution here is to do the following:

```
rm -r nodes_modules
rm package-lock.json
npm i --legacy-peer-deps
```

## Apple M1 Silicon&#x20;

When trying to run `npm run dev` on the Kwenta repository, community members with the latest M1 reported several issues with regard to the `sharp` package.&#x20;

{% hint style="success" %}
The recommended solution currently is to use Rosetta Terminal in order to avoid running into runtime errors.
{% endhint %}

There might be a possible solution by upgrading `sharp` from `v0.26` to `v0.28`.

Further possible solutions might be found here, depending on the situation:

* [https://github.com/lovell/sharp/issues/2954](https://github.com/lovell/sharp/issues/2954)
* [https://github.com/lovell/sharp/issues/2460](https://github.com/lovell/sharp/issues/2460)
* [https://github.com/lovell/sharp/issues/2460#issuecomment-751491241](https://github.com/lovell/sharp/issues/2460#issuecomment-751491241)

### How to set up the Kwenta dev environment on an Apple M1 Silicon machine

First, it is recommended to create a duplicate copy of the `Terminal` app. Open Finder > Applications > Utilities, right-click on `Terminal` and select _Duplicate_. Rename the new duplicated Terminal app to something useful, e.g. `Rosetta-Terminal`.

Right-click on the new `Rosetta-Terminal`and select _Get Info_. In the settings window popping up, make sure _Open with Rosetta_ is checked. Now open the new duplicated app.

{% hint style="info" %}
To verify if Rosetta is working, type `arch` in the Terminal. It should return `i386`.
{% endhint %}

{% hint style="warning" %}
While it is possible to run two version of homebrew and node (M1 and Rosetta), it is recommended to remove any `arm64`homebrew or node installations to avoid issues later on.
{% endhint %}

Now install the `i386`version of homebrew according to their [website instructions](https://brew.sh). It should install into the `/usr/local/homebrew` directory.

Once brew is installed, you can run `brew install npm`. You can verify that you installed the correct version by typing `node -p process.arch` which should return `x64`.

Now, you are ready to clone your fork of the Kwenta repository. If you already cloned the repository earlier, make sure to delete the `node_modules`folder. Once done, run `npm i` and start your local environment with `npm run dev`. Voila, it should work now.

If you have questions or still run into trouble, do not hesitate to join our Discord channel and ask away in the `#community-dev`channel.



## Windows

Community members on Windows reported the following issue:

```
error: cannot spawn .husky/pre-commit: Invalid argument
```

In order to fix this issue, open the `.husky/pre-commit` file in your favourite text editor and edit the following:

```git
-# #!/bin/sh
+#!/bin/sh
```

Additionally, the `.eslintrc` file might need to be changed:

```diff
    "plugins": ["prettier"],
    "rules": {
             "react/react-in-jsx-scope": "off",
-            "prettier/prettier": "error",
+           "prettier/prettier": ["error",
+            {
+                "endOfLine": "auto"
+            }
+            ],
              "no-mixed-spaces-and-tabs": ["warn", "smart-tabs"], 
```

\
