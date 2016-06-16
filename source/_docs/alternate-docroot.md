---
title: Alternate Docroot
description: Learn how to create an alternate docroot to serve your Pantheon site from.
categories: [developing,sites]
tags: [platform,code]
keywords: Composer, docroot
---

## Define alternate docroot in `pantheon.yml`
- Clone your website locally with git. If you need help check out our [Starting with Git article](https://pantheon.io/docs/git/)
- Create a `pantheon.yml file`, if it doesn't exist
- Add the line `web_docroot: true` to the top level of the YAML file, typically after `api_version`
- Add, commit and push the `pantheon.yml` file with git

### Example `pantheon.yml`
```
api_version: 1

web_docroot: true
```

### Create the `web` directory
In your code/git root create a directory named `web`. This will be the directory where your site is served from when `web_docroot: true` is defined in `pantheon.yml`.
 The directory name is not configurable. If you absolutely need a different directory name you can create a symlink with git.

### Move your site files from the code/git root to the web directory
This can be done with the `mv` command, in Finder, etc. After the files or moved use `git add -A` to add and commit the moved files and deploy them to Pantheon.

### Alternate docroot and Quicksilver
Note that if you are using a Quicksilver platform hook with the type `webphp` that the path to the script is relative to the doctroot, `web`, not the project root.

So, for example, if your `pantheon.yml` has a script location definition of `private/scripts/my_quicksilver_script.php` the file would need to be located at `web/private/scripts/my_quicksilver_script.php`.

This is because `webphp` scripts are run with Nginx, which is serving from the alternate docroot.
