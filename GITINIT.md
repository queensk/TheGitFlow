# Introduction to Git

Git is a distributed version control system that allows you to track changes in your code and collaborate with other developers. Git is widely used in software development and open source projects, such as [GitLab] and [GitHub]. In this document, you will learn some basic concepts and commands of git, as well as how to use markdown to format your text.

## What is version control?

Version control is a way of managing the history of your code. It allows you to save snapshots of your code at different points in time, and revert back to any previous version if needed. Version control also enables you to work on multiple branches of your code, and merge them together when they are ready. Version control helps you avoid losing your work, resolve conflicts, and keep track of your progress.

## What is distributed version control?

Distributed version control means that each developer has a complete copy of the code repository on their local machine. This allows them to work offline, and push or pull changes to a remote server when they are online. Distributed version control also makes it easier to collaborate with other developers, as each developer can work on their own branch, and merge their changes with the main branch when they are done.

## What is git?

Git is one of the most popular distributed version control systems. It was created by Linus Torvalds, the creator of Linux, in 2005. Git is fast, reliable, and flexible. It supports various workflows and features, such as branching, merging, rebasing, stashing, cherry-picking, tagging, and more. Git also has a large and active community that provides documentation, tutorials, tools, and support.

# Basic Git Commands

To use git, you need to install it on your computer. You can download it from [the official website], or use a package manager if you are using Linux or Mac OS. Once you have git installed, you can open a terminal or command prompt and start using git commands. Here are some of the most common git commands that you need to know:

## git init

This command creates a new git repository in the current directory. It initializes the .git folder that contains all the information about your repository. You only need to run this command once when you start a new project.

## git clone

This command copies an existing git repository from a remote server to your local machine. It creates a new directory with the same name as the repository, and downloads all the files and history from the server. You can specify the URL of the repository that you want to clone, or use a shortcut if you are using GitHub or GitLab.

For example, to clone the repository of this document from GitHub, you can run:

```bash
git clone https://github.com/queensk/TheGitFlow.git
```

Or use the shortcut:

```bash
git clone github:queensk/TheGitFlow
```

## git status

This command shows the current state of your repository. It tells you which files are staged (ready to be committed), which files are modified (changed but not staged), and which files are untracked (not part of the repository). It also tells you which branch you are on, and if you have any commits that are ahead or behind the remote server.

For example, if you run `git status` after cloning the repository of this document, you will see something like this:

```bash
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

This means that you are on the main branch, which is synchronized with the origin (the remote server), and that you have no changes in your working tree (the files in your directory).

## git add

This command adds files to the staging area, which means that they are ready to be committed. You can specify one or more files or directories that you want to add, or use a dot (.) to add all the files in the current directory.

For example, if you create a new file called `README.md` in your repository, and run `git status`, you will see something like this:

```bash
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md

nothing added to commit but untracked files present (use "git add" to track)
```

This means that `README.md` is not part of the repository yet. To add it to the staging area, you can run:

```bash
git add README.md
```

Or use a dot (.) to add all the files in the current directory:

```bash
git add .
```

If you run `git status` again after adding the file, you will see something like this:

```bash
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   README.md
```

This means that `README.md` is now staged and ready to be committed.

## git commit

This command creates a new commit, which is a snapshot of your code at a certain point in time. A commit has a message that describes what changes you have made, and a unique identifier (hash) that allows you to refer to it later. You can commit one or more files that are staged, or use the `-a` option to commit all the files that are modified.

For example, if you want to commit the `README.md` file that you have added, you can run:

```bash
git commit -m "Add README.md file"
```

The `-m` option allows you to specify the commit message in quotes. If you omit this option, git will open a text editor for you to write the message.

If you run `git status` after committing the file, you will see something like this:

```bash
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```

This means that you have created a new commit that is not yet pushed to the remote server. You can see the details of your commit by running `git log`, which will show something like this:

```bash
commit 4f6a9f8c9d7f8e8a9f8a9f8a9f8a9f8a9f8a9f8a (HEAD -> main)
Author: queensk <queenskisivuli@gmail.com>
Date:   Tue Aug 1 13:35:06 2023 +0300

    Add README.md file
```

The `HEAD` pointer indicates the current commit that you are on, and the `main` branch indicates the branch that you are on. The hash is the unique identifier of the commit, and the author and date are the information of who and when created the commit.

## git push

This command uploads your local commits to the remote server, and updates the remote branch with your changes. You can specify the name of the remote server and the name of the branch that you want to push, or use the default values if you have set them before.

For example, if you want to push your main branch to the origin server, you can run:

```bash
git push origin main
```

Or use the shortcut:

```bash
git push
```

If you run `git status` after pushing your commit, you will see something like this:

```bash
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

This means that your local branch and your remote branch are synchronized, and that you have no changes in your working tree.

## git pull

This command downloads the latest commits from the remote server, and merges them with your local branch. It is equivalent to running `git fetch` followed by `git merge`. You can specify the name of the remote server and the name of the branch that you want to pull, or use the default values if you have set them before.

For example, if you want to pull the main branch from the origin server, you can run:

```bash
git pull origin main
```

Or use the shortcut:

```bash
git pull
```

If there are no conflicts between your local branch and your remote branch, git will automatically merge them and update your working tree. If there are conflicts, git will ask you to resolve them manually before completing the merge.

## git branch

This command allows you to create, list, rename, or delete branches in your repository. A branch is a pointer to a specific commit, and it allows you to work on different features or versions of your code without affecting the main branch. You can switch between branches using `git checkout`.

For example, if you want to create a new branch called `feature`, you can run:

```bash
git branch feature
```

This will create a new branch that points to the same commit as your current branch. To see all the branches in your repository, you can run:

```bash
git branch -a
```

The `-a` option shows both local and remote branches. The output will look something like this:

```bash
  feature
* main
  remotes/origin/HEAD -> origin/main
  remotes/origin/main
```

The asterisk (\*) indicates the current branch that you are on. The `remotes/origin/HEAD` pointer indicates the default branch of the remote server.
