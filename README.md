Require ALias [![Build Status](https://travis-ci.org/pajtai/ral.png?branch=master)](https://travis-ci.org/pajtai/ral)
================

Require path aliasing.

This module allows you to easily move files and directories in your app without having to update many require calls.
Instead you update the relevant alias definition.

The paths aliases to be used are defined in `require-paths.json`. This file is found by the `ral` module using,
 `findup(process.env.REQUIRE_PATHS || '*/require-paths.json')`. The default is the root of your project, or customize
  its path using process.env.REQUIRE_PATHS.

For example if `require-paths.json` is:

```json
{
   "constants" : "lib/constants"
}
```

Then the module at `lib/constants` can be retrieved with:

```javascript
require('ral')('constants')
```

If the location of constants changes, only `require-paths.json` needs to be updated.

A path can be added after the key. For example given `constants` above:

```javascript
require('ral')('constants/something')
```

will give you `lib/constants/something`.

[Source (~20 lines)](https://github.com/pajtai/ral/blob/master/ral.js)

Release Notes:

* 2014-06-02 0.0.1 Initial Release
* 2014-06-03 0.1.0 Added tests & process.env.REQUIRE_PATHS
* 2014-06-03 0.1.1 Locking down node version to >=0.8
* 2014-06-04 0.1.2 Removing hard coded path separator
