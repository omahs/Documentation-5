---
description: Dev Environment Setup and commonly reported issues
---

# Troubleshooting

If you run into issues with the dev environment for the Kwenta dApp, please read the troubleshooting information below. If this doesn't help you further, don't hesitate to ask the devDAO community in the `#community-dev` channel for assistance!&#x20;

Please make sure you are on the latest stable (LTE) versions of `nodejs` and `npm`.

### Apple M1 Silicon&#x20;

When trying to run `npm run dev` on the Kwenta repository, community members with the latest M1 reported several issues with regard to the `sharp` package.&#x20;

{% hint style="success" %}
The recommended solution currently is to use Rosetta Terminal with node 14 in order to avoid running into runtime errors.
{% endhint %}

There might be a possible solution by upgrading `sharp` from `v0.26` to `v0.28`.

Further possible solutions might be found here, depending on the situation:

* [https://github.com/lovell/sharp/issues/2954](https://github.com/lovell/sharp/issues/2954)
* [https://github.com/lovell/sharp/issues/2460](https://github.com/lovell/sharp/issues/2460)
* [https://github.com/lovell/sharp/issues/2460#issuecomment-751491241](https://github.com/lovell/sharp/issues/2460#issuecomment-751491241)

### Windows

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
