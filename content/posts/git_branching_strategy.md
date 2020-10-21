---
title: "Git branching strategy"
date: 2020-10-21T00:43:08+05:30
draft: false
tags: ["git", "workflow"]
---

## Disclaimer

Git branching and workflow is highly opinionated, so don't take my word as gospel. This is just me stating a way of how I get things done. I won't be talking a lot about *CI/CD* and *git tags* because it's more tightly knit with one's deployment strategy, so let's just talk about branches.


## General Trivia

If you are a developer and you don't know of git, you are probably in the wrong place.
If you are a beginner and you know the basics, maybe I can give you some insights on how you can do better with git and help you optimize your workflow.

There are multiple git workflows you can find online, the one I use is a mix of multiple workflows to suit my development cycle.
I am not even sure what it is a mix of, but it just works for me.


## My Workflow

I will get to it straight.

When you layup a new repo, you are on the `master` branch.
This is the point where you make 2 more branches namely `develop` and `stage`.
You can technically just use one of those if it's a small setup.

So your git timeline might look like this now:

![initial](/images/git_branching/initial.png)


Now that you have 3 branches to keep up with, you should understand these branches.

1. `develop` branch is your branch with the latest and greatest code. All the stuff you are working is on the `develop` branch.
2. `stage` is the branch where you merge code from your `develop` branch before making it available to the world. Sorta beta phase.
3. `master` well, the master is master and it should be deployable at all times.

## Coding and Committing

When starting fresh, switch to the `master` branch using `git checkout master`.

When done, branch off to a new branch `feature/<my_new_feature>` with \
`git checkout -b feature/<my_new_feature>`


Now you go do your thing and `push` it to `feature/<my_new_feature>` \
Say you made 2 commits to the branch and pushed it.

The timeline should look like this now:

![feature](/images/git_branching/feature.png)

Even if you are a big team and collaborating over a project, you should be able to work on features independently.

Now that you have your feature branch ready, time to merge it into the `develop` branch.

checkout to the latest version of `develop` use `pull` or `fetch` if you have to,
then simply run a \
`git merge feature/<my_new_feature>` on it.

Now your timeline will look kinda like this, `m` being the `merge` commit.

![merge_develop](/images/git_branching/merge_develop.png)

For backend devs, the `develop` branch is usually connected to a smaller database and kind of mock-up services.
It's just a good idea to have a development branch before a beta test phase.

Do your tests on the `develop` branch and see if it's able to integrate with the flow of your application as expected.
Test it, reiterate through your code and refactor it.

Once done, you are ready to merge it into the `stage`.

Now, it's a good idea to make a pull request and perform a code review with your peers at this point.

Once merged on `stage`, you let your QA team(if any) test it out with an environment similar to production.
Testing your application with config similar to prod can help you mitigate unwanted last moment hassle when deploying on production.

Once approved by QA, you're ready to move stuff to production.

The cool thing about this is, you can be totally working on a new feature branch already, totally independent from the current state of stage and master.

![moving_to_prod](/images/git_branching/moving_to_prod.png)

## Playing with fire on production

Often you get weird bugs on prod that maybe last moment things you changed and now they just not work as intended.
This could've been avoided if the code was tested well and maybe something is wrong in your pipeline. Anywho, this mess you've made needs fixing, what you gonna do?

*Answer:* `hotfix` branch

How does it work?

Fork your `master` branch and make a `hotfix/<feature>` from it.
Do your thing, make your test cases pass, and merge it into `master` and on `stage` if necessary.

Something like this:

![hotfix](/images/git_branching/hotfix.png)


## Conclusion

The thing I just wrote does not mention anything about tags and CI/CD and is a very mixed sort of git workflow.
I will be covering tags and CI/CD workflow soon.

Special thanks to my colleague, [Nitin Suresh](https://twitter.com/nitinsure)
