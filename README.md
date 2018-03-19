# large-file-playground
Playground repo to explore git extensions for large files

Over the years, I've had visual assets stored in repositories or some derivative asset stored (e.g. perceptual hash). Unfortunately, there have been drawbacks (e.g. repo bloat, loss of original file). This repo is to explore the different options for storing large files in `git`

## Overview
This list from <https://www.perforce.com/blog/storing-large-binary-files-in-git-repositories> covers a very large set of options. Here's our take on them:

- [x] [git-annex](http://git-annex.branchable.com/)
    - :-1: Requires one-off commands and one-off branch for `git-annex` files
        - http://git-annex.branchable.com/tips/centralized_git_repository_tutorial/on_GitHub/
        - Would prefer "it just works" with `git add` and using `git` objects
    - :+1: Seems to still be in development
- [x] [git-lfs](https://git-lfs.github.com/)
    - :-1: Requires custom server which likely means using GitHub's server
        - GitHub's server costs $5/month, even if not many files are stored (e.g. 100kb -> $5, 5MB -> $5, 1GB -> $5)
        - Going to keep looking for something that supports S3, Google Drive, or similar
- [x] [git-bigfiles](http://caca.zoy.org/wiki/git-bigfiles)
    - :no_entry: No updates since late 2009. Not worth considering

## Unlicense
As of Mar 19 2018, Todd Wolfson has released this repository and its contents to the public domain.

It has been released under the [UNLICENSE][].

[UNLICENSE]: UNLICENSE
