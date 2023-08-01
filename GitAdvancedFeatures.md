## 1. Git Rebase

One of the most common challenges when working with git is dealing with divergent branches. When you create a new branch from the main branch and make some changes, the main branch may also receive new commits from other developers. This creates a fork in the history of the project, and when you want to merge your branch back to the main branch, you may encounter conflicts or unwanted merge commits.

Git rebase is a command that can help you avoid these problems by rewriting the history of your branch. It fetches the latest commits from the main branch and puts your changes on top of them, creating a linear and clean history. This way, you can keep your branch up to date with the main branch, and avoid unnecessary merge conflicts.

To use git rebase, you need to switch to your branch and run:

```bash
git rebase main
```

This will apply your commits one by one on top of the main branch. If there are any conflicts, git will pause the rebase and ask you to resolve them manually. Once you have resolved the conflicts, you can continue the rebase by running:

```bash
git rebase --continue
```

Alternatively, you can abort the rebase by running:

```bash
git rebase --abort
```

After the rebase is completed, you will have a new history for your branch that is based on the latest state of the main branch. However, this also means that you have changed the hashes of your commits, and if you have already pushed your branch to a remote repository, you will need to force push it by running:

```bash
git push --force-with-lease
```

This will overwrite the remote branch with your rebased branch. However, be careful when using this command, as it can cause problems for other developers who are working on the same branch. You should only use git rebase on branches that are not shared with others, or communicate with your team before doing so.

For more information on how and when to use git rebase, you can check out this article: [Merging vs. Rebasing - Atlassian Git Tutorial](^1^).

## 2. Git Cherry-Pick

Sometimes, you may want to apply a specific commit from another branch to your current branch, without merging or rebasing the whole branch. For example, you may have fixed a bug or added a feature in a different branch, and you want to bring it to your current branch without affecting other changes.

Git cherry-pick is a command that allows you to do just that. It copies a commit from another branch and creates a new commit on your current branch with the same changes. You can specify the hash of the commit that you want to cherry-pick, or use a range of commits if you want to cherry-pick multiple commits at once.

To use git cherry-pick, you need to switch to your target branch and run:

```bash
git cherry-pick <commit-hash>
```

This will create a new commit on your target branch with the same changes as the commit that you specified. If there are any conflicts, git will ask you to resolve them manually before completing the cherry-pick.

You can also use the `-n` option to apply the changes without creating a new commit, so that you can modify or combine them with other changes before committing.

For example, if you want to cherry-pick a commit from another branch called `feature`, but not create a new commit yet, you can run:

```bash
git cherry-pick -n feature
```

This will apply the changes from the latest commit on `feature` to your working tree, but not create a new commit. You can then edit or add more changes before committing.

For more information on how and when to use git cherry-pick, you can check out this article: [Five Advanced Git Concepts That Make You Look Like a Pro - Medium](^2^).

## 3. Git Reset

Another common challenge when working with git is undoing or modifying changes that you have made in your repository. Whether you want to discard some changes that you don't need anymore, or amend some changes that you have already committed, git reset is a command that can help you achieve that.

Git reset allows you to reset your working tree, staged snapshot, and/or commit history to a specific state. It has three modes: `--soft`, `--mixed`, and `--hard`, which affect different combinations of these components.

To use git reset, you need to specify the mode and the reference of the state that you want to reset to. You can use a commit hash, a branch name, a tag name, or a relative reference such as `HEAD` or `HEAD~1`.

For example, if you want to reset your working tree, staged snapshot, and commit history to the state of the previous commit, you can run:

```bash
git reset --hard HEAD~1
```

This will discard all the changes that you have made since the last commit, and move the `HEAD` pointer to the previous commit.

If you want to reset only your staged snapshot and commit history, but keep your working tree unchanged, you can run:

```bash
git reset --mixed HEAD~1
```

This will unstage all the changes that you have staged, and move the `HEAD` pointer to the previous commit. You can then edit or discard the changes in your working tree as you wish.

If you want to reset only your commit history, but keep your working tree and staged snapshot unchanged, you can run:

```bash
git reset --soft HEAD~1
```

This will move the `HEAD` pointer to the previous commit, but keep all the changes that you have made in your working tree and staged snapshot. You can then modify or combine them with other changes before committing.

For more information on how and when to use git reset, you can check out this article: [Resetting, Checking Out, and Reverting - Atlassian Git Tutorial].

## 4. Git Log

One of the most useful features of git is that it keeps a complete history of your project, which you can access at any time. However, browsing through hundreds or thousands of commits can be overwhelming and time-consuming. That's why git log is a command that can help you filter and format the output of your commit history.

Git log allows you to display the commit history of your repository in various ways. You can use various options to limit the number of commits, specify the time range, show the branches and merges, customize the output format, and more.

To use git log, you can run:

```bash
git log
```

This will show the default output of your commit history, which includes the hash, author, date, and message of each commit.

You can also use some options to modify the output. For example, if you want to see only the last five commits in your repository, you can run:

```bash
git log -5
```

The `-5` option limits the output to five commits.

If you want to see a graphical representation of your commit history, you can run:

```bash
git log --graph --oneline --decorate
```

The `--graph` option draws a text-based graph of the branches and merges. The `--oneline` option shows each commit in a single line. The `--decorate` option shows the branch and tag names that point to each commit.

For more information on how and when to use git log, you can check out this article: [Advanced Git Log - Atlassian Git Tutorial].

## 5. Git Hooks

One of the most powerful features of git is that it allows you to customize its behavior by using hooks. Hooks are scripts that run automatically when certain events occur in your repository, such as committing, pushing, merging, etc. You can use hooks to perform various tasks, such as validating code style, running tests, sending notifications, deploying code, and more.

To use git hooks, you need to create executable files in the `.git/hooks` directory of your repository. Each file corresponds to a specific hook name, such as `pre-commit`, `post-commit`, `pre-push`, etc. You can write your hooks in any scripting language that you prefer, such as bash, python, ruby, etc.

For example, if you want to create a pre-commit hook that checks if your code follows the PEP8 style guide before committing, you can create a file called `.git/hooks/pre-commit` with the following content:

```bash
#!/usr/bin/env python3

import subprocess

# Run pycodestyle on all python files in the repository
result = subprocess.run(["pycodestyle", "."], capture_output=True)

# If there are any errors or warnings, print them and abort the commit
if result.returncode != 0:
    print(result.stdout.decode())
    print("Code style check failed. Please fix the errors before committing.")
    exit(1)
```

This will run pycodestyle on all python files in your repository before each commit. If there are any errors or warnings, it will print them and abort the commit. You can then fix them and try again.

For more information on how and when to use git hooks, you can check out this article: [Git Hooks - Atlassian Git Tutorial].

## Wrapping Up

We have introduced you to five advanced git features that can make you look like a pro.

(1) Advanced Git Tutorials Overview | Atlassian Git Tutorial. https://www.atlassian.com/git/tutorials/advanced-overview.
(2) Five Advanced Git Concepts That Make You Look Like a Pro - Medium. https://livecodestream.dev/post/five-advanced-git-concepts-that-make-you-look-like-a-pro/.
(3) Advanced Git Features - Rubico. https://rubicotech.com/blog/advanced-git-features/.
