# SOURCE CONTROL HANDS ON WORKSHOP

## Table of content

- [Slide](#Slide)
- [Adding Git into your project](#Adding-Git-into-your-project)
- [Files status](#Files-status)

## Slide

https://docs.google.com/presentation/d/1cCGnm1pLVwWVn6EGceNRsQSW8wvKztiTQKo3kP4yGHU/edit?usp=sharing

### Key words from the slide

- Source Control
- Git
- GitHub

## Adding Git into your project

- Change directory to where the extracted file is located.
- Use command `git init` to initialize Git in the folder.

After adding Git into the project. You want to ensure that Git begins to see changes in your project. You can verify such behavior by using the following command.

```sh
git status
```

You should see something like the below image.

![git-status](https://user-images.githubusercontent.com/4034609/53856161-6c71fd00-4003-11e9-8e0d-c63947e63588.png)

Notice that here Git sees 2 new **untracked files**.

## Files status

### Untracked Files

Untracked files are files that are not recognized by Git.

### Tracked Files

Tracked files are files that Git keeps track of. In order for Git to start tracking the files, use the `git add <file_path>` command.

```sh
git add README.md
git add LICENSE
```

To verify that `LICENSE` and `README.md` are known by Git. Run the command `git status` again to see the result.

![git-status-new-file](https://user-images.githubusercontent.com/4034609/53856216-9cb99b80-4003-11e9-8f5f-2268205a605f.png)

#### Changes to be committed

After you added files with `git add <file path>`, those files will be put in the area call `staging`. This area is used to group related logical changes together. In this case, our logical change is "Project Initialization".

#### Create your first commit

`Commit` is the action where changes are saved as a version into the history of the project that is being control by Git. To commit the changes,

```sh
git commit -m "Project Initialization"
```

If running command above results in an error, setup your email and name so Git knows who you are.

```sh
git config --global user.email "<email>"
git config --global user.name "<name>"
```

#### View your first commit

To view the content of your commits,

```sh
git log
```

Output

```
commit fefff4be77dd084a40140e37ad0169d9e5fee87f
Author: ratthanan <nutsgmuic@gmail.com>
Date:   Sun Jan 27 13:20:15 2019 +0700

    Project Initialization
```

### Modified Files

_Git does not just track the creation and deletion of files. It also reports the changes that happen to the files that are already present in its history._

For example the content above is italic by mistake. You can easily fix them by removing `*....*` that is currently surround the content.

After remove them, save the file and run `git status` again.

![modified-files](https://user-images.githubusercontent.com/4034609/53857226-f3c16f80-4007-11e9-92ae-b364a15beebb.png)

Next, to save this change. You will have to add `README.md` into the staging area and then make a commit. Let's see if you can do it without our help.

### Files life cycle summary

![file-life-cycle](https://user-images.githubusercontent.com/11821799/51426727-375f4600-1c21-11e9-82f2-f95112e20cd1.png)

## Putting the project on remote server

Git can work fine on your local machine. However, there are situations that remote server can provide a grater benefits.

2 main drawback of working only on local machine are

- Risk of losing the code.
- Very difficult to collaborate with teammate.

Now, let's put our code up on Github server. Recalled that you already registered Github's account at the end of the presentation.

### Create a new Github repository

You can think of a repository as a place on Github's server that is available to store and look for your project.

#### 1. Go to https://www.github.com

#### 2. Click at New

![create-new-repository](https://user-images.githubusercontent.com/11821799/51798604-df8b9500-2247-11e9-901f-55f0f7f35c4d.png)

#### 3. Enter the name `source-control-hands-on-workshop` for Repository Name

#### 4. Click Create Repository

At this point, you will have a git repository on Github's server ready for storing your local copy. You will see instructions to either create a repository or push an existing repository.

#### 5. Add remote server

Follow the instructions under a section that says  
"…or push an existing repository from the command line"

For now, execute only the first line.

```sh
git remote add origin <remote_address>
```

After you finish with the command above. Your git on the local project will know which repository on Github server that it needs to be linked with.

#### 6. Pushing the repository into Github server

Right now if you look at the repository on Github, you will see that it is empty. Since there is no code that has been copied from our local machine into the remote space. We will add them using them following command.

```sh
git push -u origin master
```

_`-u` in the command link our `master` with the `master` copy on Github server. You only need to use it on the first time that you push new `branch` to the server_

(Windows) You might be asked to login after execute the command above. Just enter your Github's username and password.

Refresh your browser to see that your local machine is in sync with Github's server.

# Make use of Git

## Undoing _committed_ change

As we been mentioning since the beginning of the presentation. One of the most important benefit of using Git is the ability to see the history of your project. This will become very useful when mistake is introduced in the project and you want to traverse back in time.

### Exercise

You assume that LICENSE file is not useful so you decide to remove it.

1. Delete LICENSE file.
2. Make a commit with message "remove unused file".
3. Push it to Github.

#### Revert a commit

1. Use `git log` to see the history of the project.
2. Get the commit id(hash) of the commit where the LICENSE file is removed.
3. run command `git revert <commit id>`
4. Commit and push the change

## Undo un-committed change

1. Delete all content of README.md file.
2. Save and close your editor window
3. _Take a break_

#### Discard changes

```sh
git checkout -- <file_path>
```

# Collaboration

Up until now, only you have committed changes to the project. In collaborative work as in large software development, there are teams working on the same repository. Git helps us to maintain the synchronized state of the project.

#### Scenario

1. Go to your repository on Github.
2. Add CONTRIBUTORS.md from Github's site with the following content `This project is written by Tappasarn A.`
3. Since you start to collaborate on this project. You also want to update CONTRIBUTORS.md with your own name after the my name.
4. You see that this file is present on Github repository but not on you local machine.
5. You must sync the project.

#### Synchronize local and remote

We are certain that there is `CONTRIBUTORS.md` file in our repository as we see in Github's website, but it is not visible in the local repository.

First, check status of the our repository using

```sh
git status
```

The output indicates that we are in sync with the remote repository (origin) as below.

```
Your branch is up-to-date with 'origin/master'
```

Why ? 😭

Changes made in remote repository is not known to the local repository until you tell Git to explicitly fetch the changes. Run,

```sh
git fetch
```

Now, if you run `git status` again. You will see ....

```
Your branch is behind 'origin/master' by 1 commit, ....
```

This tells us that there is a change on remote repository that is not in our local repository. In this case it is CONTRIBUTORS.md

To bring remove changes into our local repository, Run...

```sh
git merge origin/master
```

Notice that it takes 2 commands to sync your branch with the one on the remote server. Since this is an action that developers do so often, Git provides us with the command that combines fetch and merge together.

```sh
# notice that you can only use git pull to merge from the same branch
# we will cover git branching concept in the later chapter
git pull
```

#### Merge conflict

It is also possible that remote and local repository were being edited on the same spot. With scenario like this Git needs your help to resolve conflicts.

#### Scenario

1. Make another edit on the `CONTRIBUTORS.md` by adding your university name after the contributors.
2. Make a commit (do not push yet)
3. Again, visit `github.com` and add one more contributor name at the end on the `CONTRIBUTORS.md` file.
4. Commit the change from github's website.
5. Back to your local repository, now you can try to push the commit you just made on step 2.
6. Git will tell you that pushing process is facing some problem. Can you make a guess what is wrong ?

#### Resolving merge conflict

In terminal,
![](https://user-images.githubusercontent.com/4034609/53858579-5d904800-400d-11e9-82b7-5eb16c1ca2fb.png)

In text editor,
![](https://user-images.githubusercontent.com/4034609/53858735-dd1e1700-400d-11e9-82cd-7d83b6d73205.png)

Now, you will help Git deciding on how the file supposes to be like. You remove the Git's markers (`<<<<<<<<`, `>>>>>>>`, `========`) and remove unneeded lines. Then, save the file.

If you run `git status` command it will show `CONTRIBUTORS.md` as `modified`.

In order to stay in sync with the remote repository. You would want to _stage_ and _commit_ changes from remote repository to your local repository.

How would you do that? Make sure to complete this before moving on.

#### Branching

In the real project, there will be many developers are working on the same code base.

It would be a very bad day if 5 people keep pushing there changes into the remote space. It is even worst if the push changes breaks the working project.

Git provides `branch` feature to allows developers to **encapsulate changes** that they made. Each `branch` can exist in both `local` and `remote` repository.

So each developer can be sure that the code they have written is secure and will not have effect on others' code.

##### Branching Basics

###### Creating a new branch

To create a new branch, use

```sh
git branch <branch_name>
```

You can verify that you have created a branch using the command below. You should see the <branch_name> from the previous step shows up.

```sh
git branch
```

Notice the `*` in front of `master`. This indicates that you are now working in a workspace called `master`.

You have now created a new branch. But, you have not switch your working space into the newly created one. `git status` command still reports that you are in `master branch`.

```sh
git checkout <branch_name>
```

Now, the `*` should be in front of your <branch_name>

```sh
  master
* <branch_name>
```

# Workshop

1. Create a new branch called `remove-readme`
2. After that, make sure you switch to a new branch
3. Remove `README.md` and make a commit
4. Push and create upstream for this branch. (You did it once in the beginning of the workshop.)
5. What if you want to update master branch with this change ?

### Reverting changes

At this point, your should merged your `remove-readme` branch with `master` branch and pushed the change.

`README.md` will be deleted from your repository both at `remote` and `local`.

It is important to bring the file back since it contains many important information about this workshop.

Do you recall how to revert a commit ?
