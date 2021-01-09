# Skill #3 - Command-line Git & Cloning Repositories

## I. Recap & Overview

- Last time we learned how to deploy a PHP file to Heroku, and then connect it to a GitHub repository
- We also saw how we can make changes to that PHP file utilizing GitHub's web interface, and that these changes would be propigated to Heroku automatically (so long as we have clicked the "Enable Automatic Deploys" button in Heroku's control panel)
- Editing a file in GitHub is fine if you only have one or two small changes to make, but it's not practical if you are actively working on a code project
- Instead, we are going to review:
  - how to `clone` a *remote* GitHub repository (i.e. download a local copy of it to our PC's hard drive)
  - how to make changes to this local respository
  - how to commit these changes and `push` them back to the remote repository

<hr>

## II. GitBash

- To get this done, you will need to have command line Git installed on your system, as well as a Unix Terminal emulator
- If you have a Mac:
  - you already have the Terminal application
  - head here for instructions for installing to Mac OS (note: if you have Xcode installed, then Git is already on your machine): https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
- Windows:
  - Git for Windows - https://gitforwindows.org - will install both GitBash (a terminal emulator) and command line git for you

<hr>

## III. Demo

- We'll be demoing these activities in this video -->
- Below are some of the commands we'll be using in the demo

### III-A. Unix Commands

- `cd dirName` - will change the *current working directory* to *dirName*. The current working directory is the directory we are "in" - it is where any typed in unix commands will be executed. We will call the current working directory *cwd* below
- `cd ..` - moves the *cwd* "up" one level into the parent directory of the folder
- `cd` - by itself, will change the *cwd* to the user's login (i.e. home) directory
- `pwd` - prints out the current path to the *cwd*
- `ls` - lists out files and directories in the *cwd*
- `ls -al` - lists out files and directories in the *cwd*, including "invisible" dot files
- `mkdir dirName` - will create a new folder named *dirName*
- `touch fileName` - will create an empty file named *fileName*
- `rm fileName` - will delete *fileName*
- `rmdir dirName` - will delete the folder named *dirName*
- `mv file1 file2` - will rename *file1* to *file2*
- `chmod` - used to set file permissions
- `sudo` - used to perform commands (such as installing files in system directories) as the "super user"

**Handy Unix Command-line tips**
- *ctrl-a* - to move the cursor to the *beginning* of the line
- *ctrl-e* - to move the cursor to the *end* of the line
- *up arrow* - to view previously typed commands (continue pressing up arrow to cycle through command history, the down arrow goes forward through the history)
- *tab key* - for autocompletion of partially typed file names
- *drag and drop* - files into GitBash (or Terminal) to have their file paths typed for you

### III-B. Git Commands

- `git --version` - will tell you that `git` is installed
- `git clone <url>` - will clone the remote repository at `<url>` to the *cwd*
- `git status`
- `git add` - adds local repository files to the *staging area* - see below
- `git commit -m "message"` - commits files in the staging area to the local repository files - see below
- `git push`- pushes the changes to the local repository up to the remote repository
- `git remote update`
- `git pull`

![screenshot](./_images/ss-18.png)

<hr>

## IV. HW & Submission
- Use the GitBash terminal emulator
- Create a local GitHub repository of your random joke repository by utilizing `git clone <url>`
- Make a change to the **index.php** file, such as changing `MAX_LIMIT`
- Use `git add .` to commit it to the local repository
- Use `git commit-m "message"` to commit it to the local repository
- Use `git push` to push the changes to the remote repository
- Use `git status` to be sure that your chnages and psuh was successful
- Take a screen shot of your entire session (the commands you typed above) and post it to myCourses



<hr><hr>

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
|   [Skill #1 - GitHub and Heroku](2-github-and-heroku.md) |  [**IGME-430**](../) | [**Skill #4 - **]()
