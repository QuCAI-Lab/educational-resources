# GitHub_Essentials

>![](https://github.githubassets.com/images/modules/logos_page/GitHub-Logo.png 'GitHub_Essentials')
>![](https://github.githubassets.com/images/modules/logos_page/Octocat.png) <br />
The present README is intentionally overkilling for educational purposes. It can be daunting for first-timers. <br />
**A quick walkthrough of [GitHub](https://docs.github.com/en/get-started/quickstart/hello-world) and [Git](https://docs.github.com/en/get-started/using-git/about-git) how-tos for dummies. <br /> For more information, resort to the [full reference guide to Git commands](https://git-scm.com/docs) or the [Git Cheat Sheets](https://training.github.com/).**

<br />
<br />

<div align=center>
  <b><a href="https://en.wikipedia.org/wiki/It%27s_dangerous_to_go_alone!">"It's dangerous to go alone! Take this."</a></b>
</div>

<br />


<!--- ############################################################################################################################################### -->


# Prelims

Beware: the angle brackets punctuation mark denoted by "`<>`" (voiced chevrons) is only used as a placeholder, i.e, it's not a special character.

- GitHub: a cloud-based hosting platform running on a server that ues git as its command-line tool.
- Git: an open-source version control that runs on a CLI completely independent of GitHub.

# Installing a Git GUI

One can choose to install a Git GUI in a local machine rather than using Git via Terminal. To this end, simply:

1. Download the [source tree](https://www.sourcetreeapp.com/) application.

# [Installing Git](https://github.com/git-guides/install-git) on command-line Terminal

For more information, see the [Git from source](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) guide.

## On Windows

1. Download the latest version on [gitforwindows.org](https://gitforwindows.org/);

2. Follow the instructions as provided in the Git Setup wizard as they appear.

## On Linux

For debian-based distros (Ubuntu/Ubuntu-derivatives):

```sh
sudo apt update && apt install git-all
```

And for your own sanity, install pip (a python package manager):

```bash
sudo apt update && apt install python3-pip && python3 -m pip --version
```

## With Anaconda

1. Download [Anaconda](https://www.anaconda.com/products/individual) latest version;
  - On Windows: follow the installation wizard.
  - On Linux: follow [these steps](https://github.com/QuCAI-Lab/educational-resources/tree/main/Conda_Essentials).
2. With open Anaconda command-line prompt, [simply](https://anaconda.org/anaconda/git):
```sh
conda install -c anaconda git && git --version
```
Note: the `-c` flag (abbreviated from --channel) points to the channel (Anaconda) from which git will be installed.


# [Fork](https://docs.github.com/en/get-started/quickstart/fork-a-repo)

One can choose to make a copy of a public/private GitHub repository from his own [Organization](https://docs.github.com/en/organizations/collaborating-with-groups-in-organizations/about-organizations) or someone else's GitHub account by clicking on the [Fork](https://github.com/octocat/Spoon-Knife) button. For instance, you can Fork this repository by clicking [here](https://github.com/QuCAI-Lab/educational-resources/fork).

# [Clone](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository) 

You can set up a Git linkage by cloning your private/public repository to a custom folder/directory of your Local Machine using the Command-line interface ([Unix-like](https://github.com/QuCAI-Lab/educational-resources/tree/main/Linux_Essentials) terminal or [Anaconda environment](https://github.com/QuCAI-Lab/educational-resources/tree/main/Conda_Essentials) prompt with [Git](https://anaconda.org/anaconda/git) installed), as follows:

```bash
cd <dir_pathname> && git clone https://github.com/<your_githubusername>/<repository-name>.git 
```
Note: `<dir_pathname>` is the path of the directory you wish to clone your remote repository to.

To vizualize a markdown file, one can use `grip`:

```sh
pip install grip && grip -b <filename>.md
```


<!--- ############################################################################################################################################### -->


# Git Commands

The most frequently used commands are:
- [git clone](https://git-scm.com/docs/git-clone) - To clone a remote repository into a local (on-prem) directory.
- [git branch](https://git-scm.com/docs/git-branch) - Show available branches and highlight the current branch.
- [git log](https://git-scm.com/docs/git-log) - Show the latest commits (logs).
- [git status](https://git-scm.com/docs/git-status) - Show the working tree status of the current GitHub repository.
- [git diff](https://git-scm.com/docs/git-diff) - Show differences/changes between commits.
- [git add --all](https://git-scm.com/docs/git-add) - Track all changed/new files to the staging area.
- [git commit -m "<commit_message>"](https://git-scm.com/docs/git-commit) - Record staged modifications to the local repository and define a message.
- [git remote -v](https://git-scm.com/docs/git-remote) - Show the url name of the remote repository. The standard name is "origin".
- [git push -u origin \<branch-name>](https://git-scm.com/docs/git-push) - Push your changes to a branch named `<branch-name>` from the remote (cloud-based) GitHub repository.
- [git branch \<newbranch>](https://git-scm.com/docs/git-branch) - Create a new branch named `<newbranch>`.
- [git branch](https://git-scm.com/docs/git-branch) - Show available branches.
- [git checkout \<branch-name>](https://git-scm.com/docs/git-checkout) - Switch to an existing branch named `<branch-name>`.
- [git checkout -b \<newbranch>](https://git-scm.com/docs/git-checkout) - Create a new branch named `<newbranch>` and then checkout.
- [git pull](https://git-scm.com/docs/git-pull) - a shortcut for completing both `$ git fetch` and `$ git merge` or `$ git rebase` in the same command. 

Note that `$ git checkout -b <newbranch>` is shorthand for:
```sh
$ git branch <newbranch>
$ git checkout <newbranch>
```

<!--- ############################################################################################################################################### -->


# [Git Merge](https://git-scm.com/docs/git-merge) vs [Git Rebase](https://git-scm.com/docs/git-rebase) workflow

When working collaboratively on a project, one has the choice to join two or more development histories by taking commits from a feature branch and placing on top of the header of a main (dev) branch, for example. 

**Git merge**

Git merge combines all commits from the source branch to a target branch. It creates a single merge commit (on top of the target branch header) with all changes from both target and source branches.

To merge/join previous commits from a feature branch into a brand new single merge commit placed on top of the main branch, run:
```bash
git merge <target_branch>
```
or
```bash
git merge --squash <branch-name> # To merge only the latest commits.
```
  
The above command should be followed by `git merge --abort` whenever a merge results in a conflict, and will fail if there were uncommitted changes before `git merge`. Therefore, make sure to commit all changes before running a merge.

If you get hit by the message "stopped before commiting as requested", simply run: `$ git commit -m "<commit-message>"`.
  
- Graph visualization:
```bash
   Before merge:      After merge:
                          (*) 
                           |  \
        (F)                |  (F) 
         |                 |   |
    (M)  |                (M)  |
     |  (F)                |  (F)
    (M) /                 (M) /
     |                     |
    (M)                   (M)
```

**Git rebase**

Git rebase rewinds the history of the target branch by duplicating all the commits from the source branch on top of the target branch header while leaving commits from the source branch to be garbage collected.

To rebase/move previous commits from a feature_branch to the top of the main branch, run:
```bash
git rebase <target_branch> # To do a rebase against a branch named <target_branch>.
```

- Graph visualization:
```bash
Before rebase      After rebase
                       (F)                                                    
     (F)                |   
      |                (F)  
     (F)                |  
 (M) /                 (M) 
  |                     |
 (M)                   (M)
  |                     |
 (M)                   (M)
```

**Full example:**

Rebasing against a branch named 'main'.
```bash
git clone <repo-address>.git
git checkout -b feature_branch # Create a new branch named 'feature_branch' to make changes in your local repository.
git add --all
git commit -m "<commit-message>" # Commit all changes before merge.
git checkout main # Switch to the branch 'main'.
git pull # Make sure to update your local repository in the meantime.
git checkout feature_branch # Switch back to branch 'feature_branch'.
git rebase -i main # To perform a rebase against the latest changes.
git checkout main # Switch back to branch 'main'.
git rebase -i feature_branch # To align the latest commits placing them on top of the main branch.
git push main # Push your local changes to your remote repository.
```

<!--- ############################################################################################################################################### -->

  
# [Pushing Commits](https://docs.github.com/en/get-started/using-git/pushing-commits-to-a-remote-repository) to your remote repository

- Local repository: a repository on your own computer.
- Remote repository: a repository on a GitHub server.

To push changes to an existing repository on-prem, i.e, from your local machine to your remote repository, run:
```sh
mkdir <dir_name> # Create an empty folder.
cd <dir_name> # Change directory.
git init # Initialize an empty Git repository.

git remote add origin https://github.com/<your_githubusername>/<repo-name>.git # Set a remote termed "origin" that points to the upstream repository.
git remote -v # List the configured remote.

git config user.name "<authors_name>" # Sets a Git username for the current repository (Optional).
git config user.email "authors_email@mail.com" # Sets the commit e-mail address for the current repository (Optional).

git add --all # Add all new (untracked) files to the Git staging area.
git commit -m "<commit_message>" # Define the topic of your commit.

git branch -M <newbranch> # (-m | -M) <oldbranch> is renamed to <newbranch>.
git push -u origin <newbranch> # To push local changes to your forked repository.
```

- Get your password (access token) at: `Settings` >> `Developer settings` >> `Personal access tokens` >> `Generate new token` >> `Select scopes (repo)`.

To push future updates, run:
```sh
git status # Show status of the local repository.
git diff # Show changes made to the local repo.

git add --all # Add all changes (new/untracked and modified files) to the Git staging area.
git commit -m "<commit_message>" # Define the topic of your commit.

git branch # Show the current branch.
git push -u origin <branch-name> # Push local changes to the <branch-name> branch of your remote repository.
```


<!--- ############################################################################################################################################### -->


# [Removing Files](https://git-scm.com/docs/git-rm)

To remove (delete) multiple files from both your Git repository and the current working directory:

```bash
git rm <filename1> <filename2> <filenameN>
```

To untrack a file or remove a file from the staging area of your remote repository without deleting it from the working directory of your local machine:

```bash
git rm --cached <filename>
```

To override Git **safety check**, use the `-f` or `--force` flag:

```bash
git rm -f <filename>
```

Note: Git **safety check** makes sure that the files on your current branch match those in the staging index.


<!--- ############################################################################################################################################### -->


# Adding a [.gitignore](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files) File

The `.gitignore` file instructs Git to ignore/untrack specific files or folders from a project. Common special characters:

- `*` denotes a wildcard match (placeholder);
- `/` is used to ignore pathnames relative to the .gitignore file;
- `#` denotes the comment syntax.

To add a `.gitignore` file to your cloned repository using the command-line interpreter, follow these steps.

1. Navigate to the relative/absolute path of the directory containing the cloned Git repository in your local machine:
```sh
cd <repo_pathname> 
```
2. Create a .gitignore file:
```sh
touch .gitignore
```
or simply (to open gedit text editor)
```sh
gedit .gitignore
```
Note: after saving, the file will be hidden by default, to view type `ll` in the command-line interpreter.

3. Add the file to staging area:
```
git add .gitignore
```
4. Commit changes:

```
git commit -m "<message>" .gitignore
```

- To add a `.gitignore_global` file to all Git repositories cloned in your local machine:

```sh
git config --global core.excludesfile ~/.gitignore_global
```

## Example File

```gitignore
*~

# Text files
*.txt

# virtualenv
.venv
venv/
ENV/

# Jupyter Notebook
.ipynb_checkpoints
```

For more .gitignore templates, see the [github/gitignore](https://github.com/github/gitignore) public repository.


<!--- ############################################################################################################################################### -->


# [Reverting to a Previous Version](https://git-scm.com/docs/git-reset)

- To revert your repository to the last commit:

```bash
git reset HEAD
```

- To revert your repository to a specific version:

```bash
git reset --hard <version_id> 
```
or
```bash
git reset --soft <version_id> 
```
The `-soft` flag keep all the changes in any undone command/commit.

- Creating a new branch in a specific version and checking out:

```bash
git checkout -b <newbranch> <version_hash>
```

<!--- ############################################################################################################################################### -->


# [Pulling Updates](https://docs.github.com/en/get-started/using-git/getting-changes-from-a-remote-repository) from an Upstream remote repository

If you have forked a remote repository owned by another GitHub user, there are two ways you can pull updates from said repository (a.k.a upstream repository) to sync both your local (cloned) copy and your remote forked repository.

- From the web UI:

  - **Before pull (fetch and merge):** `This branch is <N> commit(s) behind <repo-name>:<branch-name>.`

  1. Click on **Fetch upstream:** `Fetch and merge <N> upstream commit(s) from <repo-name>:<branch-name>.`

  2. Click on **Fetch and merge**. Output message should be `This branch is up to date with <repo-name>:<branch-name>.`

- From the command line:

To [sync](https://docs.github.com/github/collaborating-with-issues-and-pull-requests/syncing-a-fork) both the cloned repo and the remote forked repo:

```sh
cd <repo-name> # If you have already forked the repo. Otherwise, run 'git init' to initialize an empty local repo. 
git remote -v # To list the current configured remote repository for your fork.
git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY # Assigning "upstream" as the remote repository that will be synced with the fork.

git fetch upstream # To retrieve all the new remote-tracking branches and tags updates from the upstream repository.
git checkout <branch-name> # To switch to the existing remote-tracking branch (i.e., the branch fetched from the remote repository) named "<branch-name>".

git merge upstream/<branch-name> # To merge the specified upstream branch with your local (cloned) branch without losing your local changes.
                                 # If the local branch didn't have any commits, GIT will fast-forward the cloned repo.
                                     
git push -u origin <branch-name> # Finally, we push the local changes in order to also update your remote forked repository.
```

Alternatively, one can choose to use `$ git pull`. The full process using an empty directory thus becomes:
```sh
cd <dir-name>
git init # For an empty directory.
git remote add upstream <orig_repo_url> # Remote of the the original repo.
git remote add origin <forked_repo_url> # Remote of the forked repo.
git pull upstream <branch-name> # To fetch updates and merge them with your local (cloned) repository.
git add --all
git commit -m '<commit_message>'
git branch -M <branch-name>
git push -u origin <branch-name> # To update your remote forked repository.
```

Make sure to commit all new changes made in your local work before running the pull command to avoid a [merge conflict](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-using-the-command-line).

If you made changes to your local repository, then:
```sh
git rebase upstream/<branch-name> # To update your local (cloned) repository if it has been changed.
git push -f origin <branch-name> # To update your remote forked repository.                                
```

<!--- ############################################################################################################################################### -->


# [Issue Tracker](https://docs.github.com/en/issues/tracking-your-work-with-issues/creating-an-issue)

There are two common ways to report a bug:

1. [Create an issue](hhttps://github.com/QuCAI-Lab/educational-resources/issues/new) through the [Issue Tracker](https://github.com/QuCAI-Lab/educational-resources/issues) from the web UI.

2. Create an `issue` from your computer's command line using [GitHub CLI](https://docs.github.com/en/github-cli/github-cli/about-github-cli).


<!--- ############################################################################################################################################### -->


# [Pull Request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)

You can push changes from your forked repository to a specified branch of a remote repository owned by another GitHub user, as follows:

1 - Fork the desired repository to your GitHub account.

2 - Clone your forked repository:

```bash
git clone https://github.com/<yourgithubusername>/<repo-name>.git 
```

3 - Create a new branch for pull request and check out:

```sh
cd <repo-name>
git checkout -b <newbranch>
```

4 - Check your changes before commit:

```sh
git status
git diff
```

5 - Assigning "upstream" as the original remote repository that will be synced with the fork:

```sh
git remote -v
git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY
```

6 - Set your Local Git Identity:

```sh
git config user.name "<yourgithubusername>"
git config user.email "youremail@mail.com"
git config --list
```

7 - Push changes using your local shell/Anaconda Prompt, as follows:

```sh
git add --all
git commit -m "<topic of your pull request>"
git push -u upstream <newbranch>
```

8 - On the web UI, click the `Compare & pull request` button.

9 - Finally, click on `Create pull request`.

The admin or CI/CD tool of the upstream (original) repository will review the pull request and merge (or ignore) your proposed changes.


<!--- ############################################################################################################################################### -->


# Atom IDE

Just in case you want to skip the above command-line steps. A suggested IDE to manage your GitHub repositories on a local server is [Atom](https://atom.io/).
To install Atom on Linux, see [this manual](https://flight-manual.atom.io/getting-started/sections/installing-atom/). Once installed, you can clone, push changes, fetch/merge (pull) updates and open pull requests using the Atom GUI. 

With open Atom IDE:
- To clone: click on the `GitHub` tab >> click on the `Clone an existing GitHub repository...` tab.
- To push: click on `Git` >> click on `Stage All` >> click on `Commit to main` >> click on `Push`.
- To pull: click on `Fetch` >> click on `Pull`.


<!--- ############################################################################################################################################### -->


# Contributors 

Created and maintained by [@camponogaraviera][1].

[1]: https://github.com/camponogaraviera
