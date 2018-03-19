# large-file-playground
Playground repo to explore git extensions for large files

Over the years, I've had visual assets stored in repositories or some derivative asset stored (e.g. perceptual hash). Unfortunately, there have been drawbacks (e.g. repo bloat, loss of original file). This repo is to explore the different options for storing large files in `git`

## Overview
This list from <https://www.perforce.com/blog/storing-large-binary-files-in-git-repositories> covers a very large set of options. Here's our take on them:

## Skipped: One-off commands
Some of these projects require their own one-off commands instead of `git add` and similar. We're skipping them for now as it'd be one more thing for developers to learn

- [git-annex](http://git-annex.branchable.com/)
    - http://git-annex.branchable.com/tips/centralized_git_repository_tutorial/on_GitHub/
- [git-media](https://github.com/alebedev/git-media)
    - :question_mark: Not updated in 3 years but could be feature complete

## Skipped: Too custom
- [git-lfs](https://git-lfs.github.com/)
    - :-1: Requires custom server which likely means using GitHub's server
        - GitHub's server costs $5/month, even if not many files are stored (e.g. 100kb -> $5, 5MB -> $5, 1GB -> $5)
        - Going to keep looking for something that supports S3, Google Drive, or similar
- [git-fat](https://github.com/jedbrown/git-fat)
    - :-1: Sounds great but only supports `rsync`
        - Would prefer a 3rd party hosting service like S3, Google Drive or similar

## Unlicense
As of Mar 19 2018, Todd Wolfson has released this repository and its contents to the public domain.

It has been released under the [UNLICENSE][].

[UNLICENSE]: UNLICENSE
