# SOURCE CONTROL HANDS ON WORKSHOP

## Table of content

- [Slide](#Slide)
- [Adding Git into your project](#Adding-Git-into-your-project)
- [Files status](#Files-status)
- [Putting the project on remote server](#Putting-the-project-on-remote-server)
- [Undoing change](#Make-use-of-Git)
- [Collaboration](#Collaboration)

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

In short, you can think of `staging` as a group of prepared changes for your next commit.

#### Create your first commit

`Commit` is the action where changes are saved as a version into the history of the project that is being controlled by Git. To commit the changes,

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

At this point `commit` command has done its job, which is to store your changes in `git repository`.

### Modified Files

_Git does not just track the creation and deletion of files. It also reports the changes that happen to the files that are already present in its history._

For example the content above is italic by mistake. You can easily fix them by removing `_...._` that is currently surrounded the content.

After remove them, save the file and run `git status` again.

![modified-files](https://user-images.githubusercontent.com/4034609/53857226-f3c16f80-4007-11e9-92ae-b364a15beebb.png)

Next, to save this change. You will have to add `README.md` into the staging area and then make a commit. Let's see if you can do it without our help.

### Illustration showing a set of files being move from modified to commit

![modified](https://user-images.githubusercontent.com/11821799/164883039-62972412-cbac-4c05-90a1-11439d83c012.png)
![staged](https://user-images.githubusercontent.com/11821799/164883046-7885eb2b-9b48-4c69-a2e4-ac54dc97d023.png)
![commited](https://user-images.githubusercontent.com/11821799/164883086-134b04a1-099c-4a6d-80b1-7640b0481347.png)

### Files life cycle summary

![file-life-cycle](https://user-images.githubusercontent.com/11821799/51426727-375f4600-1c21-11e9-82f2-f95112e20cd1.png)

### Terminologies and commands summary
#### Commands
- `git init` : `adding` git into your project
- `git add` : moving files from `untracked` or `modified` to `staging` area.
- `git commit` : `saving` your changes into git timeline.
- `git log` : list out previous commits in historical order.
- `git status` : displays files that have differences between the current values in your directory and the latest commit

#### Terminologies
- `untracked` : unknown changes/files from git's point of view.
- `staged` : changes prepared in the staging area for your next commit.
- `committed` : changes stored in your git repository.
- `modified` : changes made to your project working directory.


## Putting the project on remote server

Git can work fine on your local machine. However, there are situations that remote server can provide the grater benefits.

2 main drawbacks of working only on the local machine are

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

Follow the instructions under the section that says  
"…or push an existing repository from the command line"

Before we start executing commands, let's configure a ssh public key and assign to GitHub by following the steps [here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

You can copy your project ssh link here and then apply with the below command.
![ssh-link](https://user-images.githubusercontent.com/11821799/164886040-c41135f6-4834-41be-8a48-0cbeefc531e0.png)

Execute only the first line.

```sh
git remote add origin <remote_address>
```

After you finish with the command above. Your git on the local project will know which repository on Github server that needs to be linked with.


#### 6. Pushing the repository into Github server

Right now if you look at the repository on Github, you will see that it is empty. Since there is no code that has been copied from our local machine into the remote space. We will add them using the following command.

```sh
git push -u origin master
```

_`-u` in the command link our `master` with the `master` copy on Github server. You only need to use it on the first time that you push new `branch` to the server_

(Windows) You might be asked to login after execute the command above. Just enter your Github's username and password.

Refresh your browser to see that your local machine is in sync with Github's server.

# Make use of Git

## Undoing _committed_ change

As we have been mentioning since the beginning of the presentation. One of the most important benefit of using Git is the ability to see the history of your project. This will become very useful when mistake is introduced in the project and you want to traverse back in time.

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

What just happen was you made the mistake and already committed to that mistake. We are not trying to go back in time and change the history as if the mistake never happen. However, what we are trying to do is to create another commit down into the project timeline to undo our mistake. The history still record every action that we made.
![revert-gif](https://res.cloudinary.com/practicaldev/image/fetch/s--eckmvr2M--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/3kkd2ahn41zixs12xgpf.gif) 

## Undo un-committed change

1. Delete all content of README.md file.
2. Save and close your editor window

#### Discard changes

```sh
git checkout -- <file_path>
```

As the result of this action, your changes are being discarded, and the file is going back to its unmodified state.

# Collaboration

Up until now, only you have committed changes to the project. In collaborative work as in large software development, there are teams working on the same repository. Git helps us to maintain the synchronized state of the project.

#### Scenario

1. Go to your repository on Github.
2. Add CONTRIBUTORS.md from Github's site with the following content `This project is written by Tappasarn A.`
3. Since you start to collaborate on this project. You also want to update CONTRIBUTORS.md with your own name after the my name.
4. You see that this file is presented on Github repository but not on you local machine.
5. You must sync the project.

#### Synchronize local and remote

We are certain that there is `CONTRIBUTORS.md` file in our repository as we see in Github's website, but it is not visible in the local repository.

First, check the status of the our repository using

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

![fetching-gif](https://res.cloudinary.com/practicaldev/image/fetch/s--38PuARw2--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/bulx1voegfji4vwgndh4.gif)

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

![pulling-gif](https://res.cloudinary.com/practicaldev/image/fetch/s---X5AXldj--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/zifpnl1h6a4tk4qdc9sy.gif)

#### Merge conflict

It is also possible that remote and local repository are being edited on the same spot. With the scenario like, this Git needs your help to resolve conflicts.

#### Scenario

1. Make another edit on the `CONTRIBUTORS.md` by adding your university name after the contributors.
2. Make a commit (do not push yet)
3. Again, visit `github.com` and add one more contributor name at the end on the `CONTRIBUTORS.md` file.
4. Commit the change from github's website.
5. Back to your local repository, now you can try to push the commit you just made on step 2.
6. Git will tell you that pushing process is facing some problem. Can you make a guess what is wrong ?

![conflict](https://res.cloudinary.com/practicaldev/image/fetch/s--jXqGWUai--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/m3nxmp67mqof5sa3iik9.png)

That's right multiple people can accidentally or intentionally make change on the same place. It is our job as developers to help git out and resolving the situation. 

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

In the real project, there will be many developers working on the same code base.

It would be a very bad day if 5 people keep pushing their changes into the remote space. It is even worse if the push changes break the working project.

Git provides `branch` feature to allow developers to **encapsulate changes** that they made. Each `branch` can exist in both `local` and `remote` repository.

So each developer can be sure that the code they have written is secured and will not affect on others' code.

##### Branching Basics
Basic tax application example

![branching](https://user-images.githubusercontent.com/11821799/164887856-369bd591-2439-40bd-86b0-9bd4db3ac42a.png)

This is an example of a government website project where it manages tax of Thai citizens.
The website is working fine. However, as the new year has begun. The citizens have to submit their tax form to the government.

Due to COVID-19 situation, the government has updated their refund policy. At the same time, in parallel they are also preparing for the coming year new post-COVID-19 tax calculation method.

The website is running base on the `master` branch. We cannot risk of having the website break because this is an important website that Thai citizens need to come and look up the information to prepare the tax document.

Two developer create their own branch `2021` and `2022` to work on their part from the latest code of `master`.

The branching mechanism ensures that both developers have the latest code of the running website as their base to build whatever they need.

While also ensuring that their change will not take any effect until they are ready to. 

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

You have now created a new branch. But, you have not switched your working space into the newly created one. `git status` command still reports that you are in `master branch`.

```sh
git checkout <branch_name>
```

Now, the `*` should be in front of your <branch_name>

```sh
  master
* <branch_name>
```

# Software Quality Assurance
- What if you want to update master branch with this change ?
- How do you know that your changes are ready ?
