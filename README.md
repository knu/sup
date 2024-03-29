# sup - do &lt;whatever SCM&gt; update

## NAME

`sup(1) - do <whatever SCM> update`

## SYNOPSIS

```
sup [-erq] [<path>...]
vcs [-q] [<path>...]
```

## DESCRIPTION

`sup(1)` is a tool to just "update" a working directory using whatever
SCM commands appropriate for the directory.  Updating is performed for
each given path, or the current directory if none is given.

`sup` currently supports CVS (`cvs`), Subversion (`svn`), Git
(`git`/`git-svn`), Mercurial (`hg`) and Bazaar (`bzr`).

Git-only features:

- Calls [`git-sync`](https://github.com/jacobwgillespie/git-sync) or [`hub sync`](https://github.com/mislav/hub) if they are available
- Updates remotes in parallel
- Follows the `master` to `main` switch in remotes

If called as `vcs`, the name of SCM detected is printed for each given
path.

## OPTIONS
The following command line arguments are supported:

### `-e`

Show errors only, suppressing output of successful updates.

### `-q`

Suppress warnings like "VCS unknown".

### `-r`

Update directories recursively according to a file named `.sup` which
should list the names of subdirectories to process.  Empty lines and
lines starting with `#` are ignored, lines starting with `-` or `!`
are regarded as negative patterns, and those starting with `+` or
otherwise, are regarded as positive patterns.  Surrounding space
characters are trimmed, and shell wildcards are available.

In recursion, symbolic links are ignored for security reasons.

## BUGS

-   The name obviously collides with the legendary tool "SUP"
    (Software Upgrade Protocol).

-   `sup` calls `rebase` in Git instead of `merge` and there is no way
    to configure that.

-   There is no command line option, no configuration and no nothing.

## AUTHOR

Copyright (c) 2008-2024 Akinori MUSHA.

Licensed under the 2-clause BSD license.  See `LICENSE.txt` for
details.

Visit [GitHub Repository](https://github.com/knu/sup) for the latest
information.
