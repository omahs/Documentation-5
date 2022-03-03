---
description: Dev Environment Setup and commonly reported issues
---

# Troubleshooting

If you run into issues with the dev environment for the Kwenta dApp, please read the troubleshooting information below. If this doesn't help you further, don't hesitate to ask the devDAO community in the `#community-dev` channel for assistance!&#x20;

Please make sure you are on the latest stable (LTE) versions of `nodejs` and `npm`.

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
