gitpurge
========

Shell script to purge files and folders from git history.

Attention: This will make your history incompatible with the history of others working on the repository. We assume you know this, it is the same as with rebase.


### Install


Copy the gitpurge file into e.g. /usr/bin/gitpurge. Enable executable permission.

### Usage

Backup the .git folder of the repository. Or better, backup the entire thing. Or even better: Clone or copy the repository somewhere else and work on the clone.

Open a commandline in the root of the repository.

Remove all remotes. But make sure you have everything you want to keep in local branches. This means, you might have to checkout some of the remote branches to create local follow branches.

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
