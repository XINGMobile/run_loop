## Contributing

***All pull requests should be based off the `develop` branch.***

The Calabash iOS Toolchain uses git-flow.

See these links for information about git-flow and git best practices.

Please see this [post](http://chris.beams.io/posts/git-commit/) for tips
on how to make a good commit message.

##### Git Flow Step-by-Step guide

* https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow

##### Git Best Practices

* http://justinhileman.info/article/changing-history/

##### git-flow command line tool

We don't use the git-flow tools, but this is useful anyway.

* http://danielkummer.github.io/git-flow-cheatsheet/

## Start a Feature

Start your work on a feature branch based off develop.

```
# If you don't already have the develop branch
$ git fetch origin
$ git co -t origin/develop

# If you already have the develop branch
$ git co develop
$ git pull origin develop
$ git co -b feature/my-new-feature

# Publish your branch and make a pull-request on `develop`
$ git push -u origin feature/my-new-feature
```

## Releasing

After the release branch is created:

* No more features can be added.
* All in-progress features and un-merged pull-requests must wait for the next release.
* You can, and should, make changes to the documentation.
* You can bump the gem version.

The release pull request ***must*** be made against the _master_ branch.

Be sure to check CI.

* https://travis-ci.org/calabash/run_loop
* http://ci.endoftheworl.de:8080/ # Briar jobs.

```
$ git co -b release/1.5.0

1. Update the CHANGELOG.
2. Bump the RunLoop::VERSION
3. Have a look at the README.md to see if it can be updated.

$ git push -u origin release/1.5.0

**IMPORTANT**
1. Make a pull request on GitHub on the master branch.
2. Wait for CI to finish.
3. Merge pull request.

$ git co master
$ git pull

$ gem update --system
$ rake release

$ git tag -a 1.5.0 -m"release/1.5.0"
$ git push origin 1.5.0

$ git co develop
$ git merge --no-ff release/1.5.0
$ git push

$ git branch -d release/1.5.0

Announce the release on the public channels.
```

