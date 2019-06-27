# Learning Git 
**A beginners guide to learning git for humans** 

## Review settings  

- [github pages](https://uclaioes.github.io/learning-git/)

## Configuring Git
Git has a number of configuration options. At this stage we’re concerned with two global settings: our default name and email address. This will ensure that any commits we make are associated with our details. It’s good practice to do this as later down the line, when we’re working with other people, we’ll want to know who’s committed what:

`$ git config --global user.name "Your Name"`  
`$ git config --global user.email "your.name@example.com"`

These values only need to be set once. Git will use them from now on.
To check your configuration settings enter the `config --list` command:

`$ git config --list`

```
user.name=Your Name
user.email=your.name@example.com
color.status=auto
color.branch=auto
color.interactive=auto
color.diff=auto
```


## Get started
We’re going to use the command line to work with Git. If this is something completely alien to you and you’re a little command line-phobic, don’t worry. The commands for using Git are really straightforward.

To begin with, open Terminal on your Mac. You will find Terminal in your Applications folder or by hitting Cmd + Space and typing “Terminal” into Spotlight. Once loaded, you’ll be presented with the $ prompt, which is where we type Git commands.

### ..clone a repository
When you clone a repository you take a complete copy of the entire repository including its history. 

`git clone https://github.com/uclaioes/learning-git.git`


### …or create a new repository on the command line

`$ git init` 


```
echo “# test” >> README.md
git init
git add README.md
git commit -m “first commit”
git remote add origin https://github.com/uclaioes/test.git
git push -u origin master
```

### …or push an existing repository from the command line

* Create a new repository on GitHub 
* Give your repository a name
* Connect it to a repository on local computer or clone to your desktop.

```
git remote add origin https://github.com/uclaioes/test.git
git push -u origin master
```



## Add a file and make change
We’ve initialized a Git repository within a directory that already contains files. We can find out how Git reacts using the status command:

## Add new file
- make new file in editor and save it.


`$ git status`

`$ git add filename.html`

`$ git add --all`

`$ git add * `

`$ git commit -m 'write commit message`

`$ git push`

Check out the repository to see the history. We’ve made a commit and pushed it to the server. Congrats! 

Now copy or pull those changes to your computer.
`$ git pull`


## Check remote
`git remote -v`

Change your remote's URL command.

`$ git remote set-url origin https://github.com/*USERNAME*/*REPOSITORY*.git`


## Command line 

**Create a folder from command line:**

`$ mkdir foldername`

Change directory

`$ cd [directory path]`

Check your present working directory

`$ pwd`

**List contents**

`$ ls`

Lists (ls) the contents of the current folder as well as any hidden files (-a) which are always prefixed with a dot.
`$ ls -la`

`-l` shows file and directory info
`-a` shows hidden files

## Git ignore
There are sure to be some files you’ll want to exclude from every project. 
You can do this by creating a global .gitignore file. I suggest you store this in your home directory `~/.gitignore`.

There are also a number of system files you’ll generally want to ignore. For Mac OS X, the following files are commonly excluded:
```
.DS_Store
.DS_Store?
._*
.Spotlight-V100
.Trashes
ehthumbs.db
Thumbs.db
```

To tell Git to use our global .gitignore file we add it to Git’s 
global config:

`$ git config --global core.excludesfile ~/.gitignore`


## Branching out
Branching involves diverging from your main line of development and continuing to work without affecting that main line. When you initialize a new Git repository, by default you’re checked into the master branch.

`$ git status`

`$ git checkout master`

`git checkout -b [name_of_your_new_branch]`

`git checkout -b gh-pages`

Push the branch to Github:

`$ git push origin [name_of_your_new_branch]`


### Merging branches
To merge branches, you need to be on the branch you want to merge another branch into. Because we’re going to merge the testing branch into the master branch, we need to be on master:

`$ git merge testing`

### Conflicts: Merge conflict in index.php
As always Git is very helpful – it doesn’t just spit its dummy out and leave you to scratch your head over the problem – it shows you what the problem is. We can see from this error that the conflict occurred in the index.php file. Inside that file we’ll see something like this:
```
<<<<<<< HEAD
<p>A paragraph about something interesting.</p>
=======
<h1>A heading about something interesting.</h1>
>>>>>>> testing
```

### Branch strategy
* First rule: never work directly in the master branch of a repo. 
This branch is reserved for production code, which can be deployed to a production server at any time with confidence that nothing 
will break.

I create a develop branch, typically deployed to a development server for review. I could work directly in this branch and merge it with the master, ready for deployment to production. When you’re working on small projects on your own you’ll probably find yourself spending most of your 

```
feature (feature/new-header, feature/contact-form)
bug (bug/ie-glitch, bug/184)
config (config/cache, config/database)
testing (testing/ie7, testing/contact-form)
```
* You can use as many as you like – just make sure they make sense and that you’re consistent.
* New work, new branch
* A good rule of thumb is to commit little and often. 

### A real-world scenario

Imagine you’re happily working away on your new footer. You’re an organized developer and you’ve created a new branch for the work: feature/footer. Suddenly, the client calls to tell you about a layout issue in  that prevents visitors using the contact form. 

Using `git checkout master`, you switch to the master branch. Remember the first rule: never work in the master branch directly. However, you know absolutely that the state of the files on master is exactly the same as the files on the production server (the live site). 
So you branch from master: `git checkout -b bug/ie8-contact-form`.

Now you can track down bug and squash it under your heel! Commit the fix to the repo: `git commit -am "Take that IE! Fixed contact form in IE8`".

You go back to the master branch: `git checkout master`; then you merge the bug fix branch into it: `git merge bug/ie8-contact-form`. The newly updated master branch can now be deployed to the production server. Crisis averted!

Time to go back to work on the footer: `git checkout feature/footer`. 

Unfortunately, the master branch has now diverged from the feature/footer branch; master has the fix for IE8 but feature/footer does not. That’s easily fixed by merging master into feature/footer: git merge master. Now feature/footer has everything the master branch has, plus all the work you’ve done on the footer so far.

A branching strategy affords us huge flexibility. If you’d done all your work in the master branch directly and received that call from the client you’d have been stuck!”


## Useful Links
* [Github](https://github.com/)
* [Visual Studio Code](https://code.visualstudio.com/)
* [Atom](https://atom.io/)
* [Download Git](https://git-scm.com/downloads)
* [Download Git for Windows](https://gitforwindows.org/)
* [Desktop Github app](https://desktop.github.com/)
* [Carpentries online workshop Git for Novices](http://swcarpentry.github.io/git-novice/)
* [Git for Humans](https://abookapart.com/products/git-for-humans) by David Demaree
* [Version Control with Git](https://gumroad.com/l/rXch) by Ryan Taylor
* [Git and Version Control with Tower or the Command Line](https://www.git-tower.com/learn/)
	* free ebooks, video course, cheat sheets.
* [Bitbucket](https://bitbucket.org/)
* [Gitlab](https://about.gitlab.com/)

