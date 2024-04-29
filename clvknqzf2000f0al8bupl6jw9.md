---
title: "fatal: not possible to fast-forward, aborting Error solution"
seoTitle: "fatal: not possible to fast-forward, aborting Error solution"
seoDescription: "As a developer, we often encounter error messages that can be perplexing. One such common Git error is "fatal: not possible to fast-forward, aborting."..."
datePublished: Mon Apr 29 2024 07:48:32 GMT+0000 (Coordinated Universal Time)
cuid: clvknqzf2000f0al8bupl6jw9
slug: fatal-not-possible-to-fast-forward-aborting-error-solution
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1714376416779/5a823fe1-71d2-41ae-8fab-f688521610f8.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1714376760475/c722eb96-aad8-4756-9c68-e885d2b3e331.webp
tags: programming-blogs, github, web-development, git, developer

---

As a developer, we often encounter error messages that can be perplexing. One such common Git error is "fatal: not possible to fast-forward, aborting." In this article, we will dive into this error and try to understand what this error is all about, the concept of fast-forward merges, why this error occurs, and discuss effective solutions to this error.

## Understand the error message

It is important to understand the error message Before discussing the reason and solution of the error. Understanding the error message can make our work much easier.

let's break down the error message word by word to understand its components:

The first word of the error message is "fatal". In the Git error message the word "fatal" basically means that the current operation cannot be completed, and you need to take corrective actions to resolve the issue.

"not possible to fast-forward" This segment explains the nature of the error. The message indicates that, under the current conditions, a [fast-forward](https://blog.mergify.com/what-is-a-git-merge-fast-forward/) merge is not possible.

At last The term "aborting" indicates that Git is canceling the ongoing operation. In the context of this error, Git cannot proceed with the intended merge operation due to the inability to perform a fast-forward merge.

Now if we put it all together, the error message is saying that an issue has been encountered during an attempted merge operation. The desired fast-forward merge is not possible, and Git is aborting the operation.

In real life scenario, this is a common Git error, which usually pops up when you do a Git pull from a remote branch.

> Note: A "fast-forward" merge in Git is a type of merge that occurs when the target branch (the branch being merged into) has not diverged from the source branch (the branch being merged) since the last commit and can be directly updated with the new commits from another branch.
> 
> By default git always try to perform fast-forward merge if the feature branch contains a sequence of commits that can be “joined” to the current main branch, then Git will “fast-forward” those commits into main, instead of merge.
> 
> A fast-forward merge is recommended to be used for complex conflicts. Instead, you should use other ways to merge them.

## The reason for fast-forward is not possible

If there are Divergent Histories or Diverging branches then the fast-forward commit is not possible.

In the context of Git, divergent changes refer to alterations made independently on both the branch being merged (feature\_branch) and the target branch (main).

For example: Let's imagine the situation where someone adds a commit to the remote branch and at the same time you add a commit to the local branch.

Now when you run git pull in this situation. Git will try to fast-forward those commits but it won't be able to do that and will run a 'fatal: not possible to fast-forward, aborting' error. Because there is an extra commit on the local branch that doesn’t exist on the remote branch.

In short, When two branches have separate commit histories that don't form a linear sequence, Git cannot perform a fast-forward merge.

## Possible Fixes for the error

There is no magic fix for the "fatal: Not possible to fast-forward, aborting" error. Your approach depends on what you're aiming for.

Here are some common options:

### Changing the default settings

One simple way we can apply to solve error is changing the default behavior of git prevent fast-forward merges and always create a new merge commit, even in cases where a fast-forward is possible.

To inspect the configuration and determine whether the pull.ff setting is configured to only, developers can use the following commands: Check pull.ff Setting:

```bash
git config pull.ff
```

> If you don't get any output after running this command, it typically indicates that the pull.ff configuration setting is not defined in any of the configuration files. Git will then fall back to its default behavior for handling merges when pulling changes.

To change the pull.ff (git pull regarding fast-forward merges) configuration, you can use the following commands:

Remove Default Setting:

```bash
git config --unset pull.ff
```

Set pull.ff to Another Value (e.g., true for [rebase](https://git-scm.com/docs/git-rebase)):

```bash
git config pull.ff true
```

Adjusting the configuration might be necessary based on the project's requirements or the preferred merging strategy. If a project involves workflows where non-fast-forward merges are acceptable or necessary, developers might choose to configure pull.ff differently.

### Making commit manually (rebase/merge)

[Merge](https://www.w3schools.com/git/git_branch_merge.asp?remote=github) commits are a tremendously useful tool in Git, but they can also add a layer of complexity. That is why it is better to create a merge commit manually without depending on Git to automatically do it for you by changing the default settings.

let's see an example situation and how to solve it.

For example: You're working on a feature branch called feature/new-feature where you've made several commits to implement a new feature. Meanwhile, the main branch has also progressed with new commits from other team members. Now you decide to integrate the changes from the main branch into your `feature/new-feature` branch to ensure your feature is up-to-date with the latest changes. You run `git pull origin main` while on the `feature/new-feature` branch to pull changes from the main branch. but you got the error `fatal: Not possible to fast-forward, aborting`

We can solve this issue in two ways. Let's see both of them:

1. Rebase Your Commits:
    
    Rebasing is an important Git topic that deserves an entire article of its own. In short, It essentially rewrites the commit history by placing your changes on top of the latest changes from another branch. This helps to create a linear project history and can facilitate smoother integration of changes from different branches.
    
    ![git rebase](https://cdn.hashnode.com/res/hashnode/image/upload/v1714376448169/2fb2fb21-0574-4df7-b940-e4771fc5ae9d.webp align="center")
    
    If you want to maintain a clean and linear history without unnecessary merge commits, rebasing is a good choice.
    
    To solve the issue using rebase, first of all, Determine which branch you want to merge your changes into. This is typically the branch you want to update with your changes, such as the main.
    
    Use the git rebase command to reapply your local commits onto the target branch. Here's how you can do it:
    
    ```bash
    git checkout feature/new-feature git rebase main
    ```
    
    This command sequence switches to your feature branch (`feature/new-feature`) and then release your commits onto the `main` branch. If there are conflicts between your changes and the changes on the target branch (`main`), Git will pause the rebase process and prompt you to resolve these conflicts manually. You'll need to edit the conflicted files, stage the changes, and continue the rebase process until all conflicts are resolved.
    
    Once all conflicts are resolved, you can continue the rebase process by using the following command:
    
    ```bash
    git rebase --continue
    ```
    
    This command tells Git to continue applying the remaining commits in the rebase operation.
    
    Finally, push the rebased changes to the remote repository if applicable, using git push. Since you've rewritten history with the rebased commits, you may need to force-push if you've already pushed your feature branch to the remote repository:
    
    ```bash
    git push origin feature/new-feature --force
    ```
    
    However, force-pushing can be risky, especially if others are also working on the same branch. If someone else has pulled the branch before you force-push, their local copy of the branch will become out of sync with the remote repository, leading to potential confusion and conflicts.
    
2. Perform a Regular Merge:
    
    Regular merging creates a merge commit that explicitly shows the merge point and preserves the individual commit history of both branches.
    
    ![git merge](https://cdn.hashnode.com/res/hashnode/image/upload/v1714376491456/60f3a7cd-4c6c-4917-97ee-a033bedb7f30.webp align="center")
    
    If maintaining the independence of branches and clearly documenting points of divergence and integration is important, regular merging is a better choice.
    
    Switch to the target branch you want to merge into Using git checkout or git switch
    
    ```bash
    git checkout feature/new-feature
    ```
    
    Use git merge to merge the source branch into the target branch. Git will create a merge commit to reconcile the changes.
    
    ```bash
    git merge source_branch
    ```
    
    If Git encounters conflicts during the merge, you'll need to resolve them manually.
    
    After resolving conflicts, commit the changes.
    
    ```bash
    git commit -m "Merge branch 'source_branch' into 'target_branch'"
    ```
    
    If you're working with a remote repository, don't forget to push the changes.
    
    ```bash
    git push origin target_branch
    ```
    
    these should solve the error.
    
    > When faced with the "fatal: not possible to fast-forward, aborting" error in Git, developers need to explore the commit history and identify the divergence between their current branch and the target branch.
    > 
    > To understand the divergence, utilize the following command to view the commit history of both your current branch and the target branch:
    > 
    > ```bash
    > git log --graph --oneline HEAD <some/branch>
    > ```
    > 
    > This command provides a graphical representation of the commit history, highlighting any divergent changes between the two branches.
    

## Resources

* [Git merge](https://www.atlassian.com/git/tutorials/using-branches/git-merge)
    
* [How I fixed “fatal: Not possible to fast-forward, aborting”](https://linuxpip.org/fix-fatal-not-possible-to-fast-forward-aborting-in-git)
    
* [Git warning: Pulling without specifying how to reconcile divergent branches is discouraged](https://salferrarello.com/git-warning-pulling-without-specifying-how-to-reconcile-divergent-branches-is-discouraged/)