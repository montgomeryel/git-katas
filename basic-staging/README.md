# Git Kata: Basic Staging

This kata will examine the staging area of git.

In git we are working with three different areas:

* The working directory where you are making your changes
* The staging area where all changes you have added through `git add` will stay
* The repository where every commit ends up, making your history. To put your staged changes in here you issue the `git commit` command.

A file can have changes both in the working directory and staging area at the same time.
These changes do not have to be the same.

We will also work with `git restore` to restore the staged changes of a file, and `git checkout` to return a file to a previous state.

## Setup

1. Run `source setup.sh` (or `.\setup.ps1` in PowerShell)

## The task

You live in your own repository. There is a file called `file.txt`.

1. What's the content of `file.txt`? the number 2
2. Overwrite the content in `file.txt`: `echo 2 > file.txt` to change the state of your file in the working directory (or `sc file.txt '2'` in PowerShell)
3. What does `git diff` tell you? this shows the difference between staging area and working directory. the file now contains a 2.  It indicates that file.txt has changed but isn’t yet staged. 
 diff --git a/file.txt b/file.txt
index d00491f..c7250cb 100644
Binary files a/file.txt and b/file.txt differ
4. What does `git diff --staged` tell you? why is this blank? diff between staged area and last commit
blank because file.txt isn't yet staged
5. Run `git add file.txt` to stage your changes from the working directory. This stages the changes in file.txt
6. What does `git diff` tell you? blank. Now it shows nothing (blank output) since there are no differences between the working directory and the staging area (they’re both the same).
7. What does `git diff --staged` tell you? It now shows the differences between the staged area and the last commit, indicating that file.txt has changed:
8. Overwrite the content in `file.txt`: `echo 3 > file.txt` to change the state of your file in the working directory (or `sc file.txt '3'` in PowerShell). This changes the working directory’s file.txt to 3, so the working directory differs from both the staging area and the last commit. Shows differences between the working directory and the staging area.
9. What does `git diff` tell you?
10. What does `git diff --staged` tell you? Shows differences between the staging area and the last commit.
diff --git a/file.txt b/file.txt
index d00491f..c7250cb 100644
Binary files a/file.txt and b/file.txt differ
11. Explain what is happening
    The setup.sh (or setup.ps1) script prepares the environment.

    echo commands change file.txt’s content, altering its state in the working directory.

    git diff shows the working directory vs. the staging area.

    git diff --staged shows the staging area vs. the last commit.

    git add stages the changes, moving them from the working directory to the staging area.
12. Run `git status` and observe that `file.txt` are present twice in the output.
13. Run `git restore --staged file.txt` to unstage the change
14. What does `git status` tell you now?
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   file.txt
15. Stage the change and make a commit
git add file.txt
git commit -m "commit message"
16. What does the log look like? git log
17. Overwrite the content in `file.txt`: `echo 4 > file.txt` (or `sc file.txt '4'` in PowerShell)
18. What is the content of `file.txt`? 4
19. What does `git status` tell us?
20. Run `git restore file.txt`
21. What is the content of `file.txt`? 3
22. What does `git status` tell us?

## Useful commands

- `git add`
- `git commit`
- `git commit -m "My lazy short commit message"`
- `git log`
- `git log -n 5`
- `git log --oneline`
- `git log --oneline --graph`
- `git restore --staged`

## Aliases

You can set up aliases as such:
`git config --global alias.lol 'log --oneline --graph --all'`
This might be useful to you.
