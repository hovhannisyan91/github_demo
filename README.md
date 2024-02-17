# Git and GitHub 


## Installation and Configuration

### Installation

- **MacOS:** There is a need to install *Xcode Command Line Tools* open the terminal and type `xcode-select --install`
- **Linux:** Usually it should be there, however you can install by typing the following commands on terminal`sudo apt install git`
- **Windows:** download git installer from [here](https://git-scm.com/download/win) and install it with default properties

In order to check git is properly installed, just type `git` in your terminal.


### Configuration


1. to check current git config `git config --global --list`
2. `git config --global user.name  your_name`
3. `git config --global user.email your_email`
4. check the config file update `git config --global --list`

### Generate Access Token

During the first `push`, you might be asked to provide a `password`, however GitHub accepts access token instead of a password. To generate a personal access token for GitHub, follow these steps:

1. Sign in to your GitHub account: Go to the GitHub website (https://github.com/) and sign in if you haven't already.

2. Access token settings: Click on your `profile` icon in the top right corner of the page, then click on `Settings>>Developer settings>>Personal access tokens>>Generate new token`
3. Select scopes
4. Generate token
5. Copy token: Once the token is generated, you'll see it displayed on the page. 

#### Generate SSH Key

1. Open a terminal or command prompt on your computer.
1. Use the ssh-keygen command to generate a new SSH key. You can do this by typing the following command and pressing Enter:

    `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
3. You will be prompted to choose the location to save the SSH key. Press Enter to save it in the default location (~/.ssh/id_rsa) or specify a different location if you prefer.
4. You'll also be prompted to enter a passphrase for added security. You can either enter a passphrase or leave it blank if you don't want to use one. Note that leaving the passphrase blank makes your SSH key less secure.
5. Once the key is generated, you'll see a message indicating where the key has been saved, typically something like: *your public key has been saved in "path"*
6. Now, you need to add your SSH key to your GitHub account. You can do this by copying the contents of the public key (id_rsa.pub). You can use the cat command to display the contents of the file and then copy it: 
    - view the key: `cat ~/.ssh/id_rsa.pub`
    - copy the key `pbcopy ~/.ssh/id_rsa.pub`
    - Go to the `GitHub Page>Settings>SSH and GPG Keys>> New SSH key` and paste the SSH key and press `add ssh key`





## Main flow

### Initializng git Repo

- **Initializng repo** -> `git _init_`
- **Clonning** ->  `git clone your_git_link`

- **Displaying the current state of the repository** ->  `git status`
    - **Untracked** -> Files that are not yet tracked by Git. 
    - **Modified** -> Files that have been changed since the last commit but have not been staged.
    - **Staged** -> Files that have been added to the staging area and are ready to be committed.
    - **Unmodified** -> Files that have not been changed since the last commit.
- **Adding files to staging** ->  `git add .` or `git add your_filename`
- **Commiting the change** ->  `git commit -m "comment"`
- **Above two steps in one line** ->  `git commit -am "comment"` 
- **Display a list of commits in a Git repository** -> `git log`
- **Display a list of commits in a Git repository with detailed information** -> `git log -p`
- **Display detailed information about the latest commit in your current branch** -> `git show`
- **Display detailed information about a specific commit** -> `git show your_commit_hash`
- **Restore the specified file to its state in the last commit** -> `git restore your_file`
- **Restore all files in the working directory to their state in the last commit** -> `git restore .`
- **Unstage all changes that have been previously staged for the next commit** -> `git restore --staged .`
- **Unstage the specified file that have been previously staged for the next commit** -> `git restore --staged file_name`
- **Show the changes between**
    - **the current state of files in your working directory and the last commit** -> `git diff`
    - **the files in the staging area and the last commit** -> `git diff --cached`
    - **two commits** -> `git diff commit1 commit2`
    - **two specific files** -> `git diff file1 file2`
- **Rename a file** -> `git mv old_file_name new_file_name`
- **Move a file to a different directory** -> `git mv source_path other_path`
- **Delete file from the working directory** -> `git rm file_name`


## Branches

- **List of existing branches:** `git branch -a`
- **Create new branch:** `git branch branch_name`
- **Create and swithche to at the same time:** `git checkout -b branch_name`
- **Swithiche within branches:** `git checkout branch_name`
- **Raname branch:** `git branch -m old_branch new_branch`
- **Delete branch:** `git branch -d branch_name` *you must be in different branch*
- **Merge changes from one branch into another** -> `git merge branch_name`
- **Show the differences between the current branch and the specified branch_name** -> `git diff branch_name`

## Connection to remote repositories

- **Add a new remote repository** -> `git remote add origin link_repository`
- **List all the remote repositories** -> `git remote -v`
- **Display detailed information about the specified remote repository** -> `git remote show repo_name`
- **Push changes to the  branch of the remote repository** `git push origin branch_name`
- **Pull changes from the  branch of the remote repository** -> `git pull`
- **Fetch the latest changes from the  branch of the remote repository** -> `git fetch origin branch_name`
- **To get the resulting changes into a local branch, you should use** -> `git merge origin/branch_name`
  
## Tags

- **Create a lightweight tag at the current commit** -> `git tag tag_name`
- **Create an annotated tag with a message** -> `git tag -a tag_name -m "Tag message"`
- **List all tags in the repository** -> `git tag`
- **List of filtered tags based on a specific pattern** -> `git tag -l "pattern"`
- **Delete the specified tag from the repository** -> `git tag -d tag_name`
- **Push the specified tag to the remote repository** -> `git push origin tag_name`
- **Push all tags to the remote repository** -> `git push origin --tags`


## Gitignore

The `.gitignore` file is a text file used by Git to specify intentionally untracked files that Git should ignore. These files typically contain patterns indicating which files or directories Git should ignore when tracking changes in your repository.

- ignoring a folder `foldername\`
- ignoring by  file type `*.csv`

Note, if you want to ignore a file which is available on remote, first there is a need to delete the cache:

1. `git rm --cached filename`
2. `git commit -m "Update .gitignore to ignore .DS_Store files"`
3. `git push origin <branch-name>`

