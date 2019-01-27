# SOURCE CONTROL HANDS ON WORKSHOP

## Table of content

* [Slide](#Slide)
* [Adding Git into your project](#Adding-Git-into-your-project)
* [Files status](#Files-status)

## Slide
https://docs.google.com/presentation/d/1cCGnm1pLVwWVn6EGceNRsQSW8wvKztiTQKo3kP4yGHU/edit?usp=sharing

### Key words from the slide
* Source Control
* Git
* GitHub

## Adding Git into your project
* Right click at the folder you just extracted.
* Click at `Git Bash here`.
* Type command `git init` to start using Git in the following folder.

After adding Git into the project. You want to ensure that Git begins to see changes in your project. You can verify such behavior by using the following command.

```sh
git status
```
 On your bash screen, you should see something like the below image.

 ![git-status](https://user-images.githubusercontent.com/4034609/51797523-e6aaa700-2237-11e9-8f04-50d640936fbb.png)

 Notice that here Git sees 2 new untracked files.

## Files status
### Untracked Files
Untracked files are files that are not recognized by Git. In our case, Git has just been added into the project that is the reason why it does not know any of the files here.

### Tracked Files
Tracked files are files that Git keeps track of. In order for Git to start tracking the files, using `git add <file_path>` command.
```sh
git add README.md
git add LICENSE
```
To verify that `LICENSE` and `README.md` are known by Git. Run the command `git status` again to see the result.

![git-status-new-file](https://user-images.githubusercontent.com/4034609/51797637-afd59080-2239-11e9-8cdc-ccf050d6e06c.png)

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
*Git does not just track the creation and deletion of files. It also reports the changes that happen to the files that are already present in its history.*

For example the content above is italic by mistake. You can easily fix them by removing `*....*` that is currently surround the content.

After remove them, save the file and run `git status` again.

![modified-files](https://user-images.githubusercontent.com/4034609/51798170-02ff1180-2241-11e9-8c51-259a7cabba58.png)

Next, to save this change. You will have to add `README.md` into the staging area and then make a commit. Let's see if you can do it without our help. 

### Files life cycle summary
![file-life-cycle](https://user-images.githubusercontent.com/11821799/51426727-375f4600-1c21-11e9-82f2-f95112e20cd1.png)

## Putting the project on remote server
Git can work fine on your local machine. However, there are situations that remote server can provide a grater benefits.

2 main drawback of working only on local machine are 
* Risk of losing the code.
* Very difficult to collaborate with teammate.

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

After you finish with the command above. Your git on the local project will knows which repository on Github server that it need to be linked with.

#### 6. Pushing the repository into Github server
Right now if you look at the repository on Github, you will see that it is empty. Since there is no code that has been copied from our local machine into the remote space. We will add them using them following command.

```sh
git push -u origin master
```
*`-u` in the command link our `master` with the `master` copy on Github server. You only need to use it on the first time that you push new `branch` to the server* 

(Windows) You might be asked to login after execute the command above. Just enter your Github's username and password.

Refresh your browser to see that your local machine is in sync with Github's server.

### Revert you change
As we been mentioning since the beginning of the presentation. One of the most important benefit of using Git is the ability to see the history of your project. This will become very useful when mistake is introduce in the project and you want to traverse back in time.

#### Exercise

You assume that LICENSE file is not useful so you decide to remove it.

1. Delete LICENSE file.
2. Make a commit with message "remove unused file".
3. Push it to Github.

#### Git revert
1. Use `git log` to see the history of the project.
2. Get the commit id of the commit where the LICENSE file is removed.
3. run command `git revert <commit id>`
4. Commit and push the change