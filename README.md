# large-file-playground
Playground repo to explore git extensions for large files

Over the years, I've had visual assets stored in repositories or some derivative asset stored (e.g. perceptual hash). Unfortunately, there have been drawbacks (e.g. repo bloat, loss of original file). This repo is to explore the different options for storing large files in `git`

## Overview
This list from <https://www.perforce.com/blog/storing-large-binary-files-in-git-repositories> covers a very large set of options. Here's our take on them:

### Skipped: One-off commands
Some of these projects require their own one-off commands instead of `git add` and similar. We're skipping them for now as it'd be one more thing for developers to learn

- [git-annex](http://git-annex.branchable.com/)
    - http://git-annex.branchable.com/tips/centralized_git_repository_tutorial/on_GitHub/
- [git-media](https://github.com/alebedev/git-media)
    - :question_mark: Not updated in 3 years but could be feature complete

### Skipped: Not third party
We've skipped these projects due to requiring a non-3rd party hosting service (e.g. `rsync` server, `git-lfs` server). We might revisit them but we're prioritzing projects that support services like S3, Google Drive, or similar first

- [git-lfs](https://git-lfs.github.com/)
    - :-1: Requires custom server which likely means using GitHub's server
        - GitHub's server costs $5/month, even if not many files are stored (e.g. 100kb -> $5, 5MB -> $5, 1GB -> $5)
- [git-fat](https://github.com/jedbrown/git-fat)
    - :-1: Sounds great but only supports `rsync`

### Rejected
- [git-bigfiles](http://caca.zoy.org/wiki/git-bigfiles)
    - :no_entry: No updates since 2009
- [git-sym](https://github.com/cdunn2001/git-sym)
    - :no_entry: No data integrity guarantee

### Pending exploration
- [git-bigstore](https://github.com/lionheart/git-bigstore)
    - Looks great, let's check it out (purpose of this repo)
    - Has some global dependencies due to `pip`, not a lot but some
        ```
        boto==2.48.0
        boto3==1.6.11
        botocore==1.9.11
        docutils==0.14
        futures==3.2.0
        git-bigstore==1.0.1
        gitdb==0.6.4
        GitPython==1.0.2
        jmespath==0.9.3
        python-cloudfiles==1.7.11
        python-dateutil==2.7.0
        pytz==2018.3
        s3transfer==0.1.13
        six==1.11.0
        smmap==0.9.0
        ```
    - Created S3 bucket `twolfson-git-large-files` with explicit policy under group
        ```
        {
            "Version": "2012-10-17",
            "Statement": [
                {
                    "Sid": "AllowS3TwolfsonGitLargeFilesAccess",
                    "Effect": "Allow",
                    "Action": "s3:*",
                    "Resource": [
                        "arn:aws:s3:::twolfson-git-large-files",
                        "arn:aws:s3:::twolfson-git-large-files/*"
                    ]
                }
            ]
        }
        ```

## Unlicense
As of Mar 19 2018, Todd Wolfson has released this repository and its contents to the public domain.

It has been released under the [UNLICENSE][].

[UNLICENSE]: UNLICENSE
