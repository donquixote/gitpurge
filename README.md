gitpurge
========

Shell script to purge files and folders from git history.


Install
=======

Copy the gitpurge file into e.g. /usr/bin/gitpurge. Enable executable permission.

Usage
======

Backup the .git folder of the repository. Or better, backup the entire thing.

Open a commandline in the root of the repository.

Assume you want to purge these files and folders (example from Drupal):
- htdocs/sites/a.com/files
- htdocs/sites/b.com/files
- htdocs/sites/a.com/settings.php
- htdocs/sites/b.com/settings.php
- oldfolder
- otheroldfolder
- "folder name with space"

Simple way:

    $ gitpurge htdocs/sites/a.com/files htdocs/sites/b.com/files htdocs/sites/a.com/settings.php htdocs/sites/b.com/settings.php oldfolder otheroldfolder folder\ name\ with\ space

Smart way with less typing:

    $ gitpurge htdocs/sites/{a.com,b.com}/{files,settings.php} oldfolder otheroldfolder folder\ name\ with\ space

The second way can be especially useful if you have many folders that share a common pattern.

Attention:
The '\*' wildcard is NOT RELIABLE because it only works in commits where the files exist physically in the filesystem. So, "htdocs/sites/\*/files" does NOT do the trick!
