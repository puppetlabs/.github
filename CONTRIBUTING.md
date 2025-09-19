# How to contribute

Third-party patches are essential for keeping Puppet great. We simply can't
access the huge number of platforms and myriad configurations for running
Puppet. We want to keep it as easy as possible to contribute changes that
get things working in your environment. There are a few guidelines that we
need contributors to follow so that we can have a chance of keeping on
top of things.

## Puppet Core vs Modules

New functionality is typically directed toward modules to provide a slimmer
Puppet Core, reducing its surface area, and to allow greater freedom for
module maintainers to ship releases at their own cadence, rather than
being held to the cadence of Puppet releases. With Puppet 4's "all in one"
packaging, a list of modules at specific versions will be packaged with the
core so that popular types and providers will still be available as part of
the "out of the box" experience.

Generally, new types and new OS-specific providers for existing types should
be added in modules. Exceptions would be things like new cross-OS providers
and updates to existing core types.

If you are unsure of whether your contribution should be implemented as a
module or part of Puppet Core, you may visit [#puppet-dev on slack](https://slack.puppet.com/), or ask on
the [puppet-dev mailing list](https://groups.google.com/forum/#!forum/puppet-dev) for advice.

## Getting Started

* Make sure you have a [GitHub account](https://github.com/signup/free).
* (Optional) Submit a GitHub Issue if one does not already exist.
  * Clearly describe the issue including steps to reproduce when it is a bug.
  * Make sure you fill in the earliest version that you know has the issue.
* Fork the repository on GitHub.

## Making Changes

* Create a topic branch from where you want to base your work.
  * For new and active repositories, this is usually the `main` branch, but for
    older or less active repos, the default branch may still be named `master`.
  * Only target branches other than the default if you are certain your fix must
    be on that branch.
  * To quickly create a topic branch based on the default branch, run `git
    checkout -b fix/main/my_contribution main` (or `master` for older repos).
    Please avoid working directly on the default branch.
* Make commits of atomic units.
  * Your commit message should clearly describe how the behavior is changing and why.
  * Commit messages that say "fixes bug" or are empty will be rejected.
  * If code changes cause tests to fail, then the tests should be updated in the
    same commit as the code changes.
  * Squash intermediate commits.
  * Do not create merge commits in your pull request. Instead rebase your pull
    request. For example, if your feature branch tracks `upstream/main`, then
    run `git rebase $(git merge-base HEAD upstream/main) --onto upstream/main`
    and force push to your remote `git push --force origin HEAD`.
* Make commits of logical units.
  * Significant whitespace-only changes should be made in a single commit, not
    comingled with non-whitespace changes.
  * For significant changes, break down your work in separate commits to make it
    easier to review.
  * If your pull request contains multiple commits, then tests should pass at each
    stage. To confirm, assuming your feature branch tracks `upstream/main`, then run
    `git rebase -i $(git merge-base HEAD upstream/main) --exec 'bundle exec rake <task>'`
* Check for unnecessary whitespace with `git diff --check` before committing.
* Make sure your commit messages are in the proper format. We use the [50/72 rule](https://git-scm.com/book/en/v2/Distributed-Git-Contributing-to-a-Project) in commit messages.

  ```text
      Make the example in CONTRIBUTING imperative and concrete

      Without this patch applied the example commit message in the CONTRIBUTING
      document is not a concrete example. This is a problem because the
      contributor is left to imagine what the commit message should look like
      based on a description rather than an example. This patch fixes the
      problem by making the example concrete and imperative.

      The first line is a real-life imperative statement. The body describes
      the behavior without the patch, why this is a problem, and how the
      patch fixes the problem when applied.
  ```

* Make sure you have added the necessary tests for your changes.
* For details on how to run tests, please see [the quickstart guide](https://github.com/puppetlabs/puppet/blob/main/docs/quickstart.md)

## Submitting Changes

* Push your changes to a topic branch in your fork of the repository.
* Submit a pull request to the repository in the puppetlabs organization.
  * Sign the CLA when prompted to via a PR comment.
* If a GitHub Issues exists [link to it](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue) to indicate that your PR addresses this issue.
* After feedback has been given we expect responses within two weeks. After two
  weeks we may close the pull request if it isn't showing any activity.

## Revert Policy

By running tests in advance and by engaging with peer review for prospective
changes, your contributions have a high probability of becoming long lived
parts of the the project. After being merged, the code will run through a
series of testing pipelines on a large number of operating system
environments. These pipelines can reveal incompatibilities that are difficult
to detect in advance.

If the code change results in a test failure, we will make our best effort to
correct the error. If a fix cannot be determined and committed within 24 hours
of its discovery, the commit(s) responsible _may_ be reverted, at the
discretion of the committer and Puppet maintainers. This action would be taken
to help maintain passing states in our testing pipelines.

The original contributor will be notified of the revert in a comment the PR or
issue associated with the change. A reference to the test(s) and operating
system(s) that failed as a result of the code change will also be added to the
comment. This test(s) should be used to check future submissions of the code to
ensure the issue has been resolved.

### Summary

* Changes resulting in test pipeline failures will be reverted if they cannot
  be resolved within one business day.

## Additional Resources

* [Puppet community guidelines](https://puppet.com/community/community-guidelines)
* [Contributor License Agreement](https://puppet.com/community/contributor-license-agreement)
* [General GitHub documentation](https://help.github.com/)
* [GitHub pull request documentation](https://help.github.com/articles/creating-a-pull-request/)
* [Puppet Community Slack](https://slack.puppet.com)
* [puppet-dev mailing list](https://groups.google.com/forum/#!forum/puppet-dev)
