# SOURCE CONTROL HANDS ON WORKSHOP

## Table of content

* [Slide](#Slide)
* [Overall Git's structure](#Overall-Git's-structure)

## Slide
https://docs.google.com/presentation/d/1cCGnm1pLVwWVn6EGceNRsQSW8wvKztiTQKo3kP4yGHU/edit?usp=sharing

### Key words from the slide
* Source Control
* Git
* GitHub
* Fork
* Clone

Some of the key words that you have gone through from the slide above might not yet been explained. But at the end of the workshop, I can promise, it will be crystal clear to you.

## Overall Git's structure
We now know that the practice of using source control is very beneficial to the project. However, it would not be a clever idea if you have to create your own version control system. And this is where Git shines.

### Remote VS Local
Git uses `Distributed Version Control Systems` as it structure so the history of your project is not only stored on the server, but on the local machine as you have clone the project. At the end of the presentation slide, you visited your repository on GitHub's website. That was where your remote history of the project reside. Later, you used the command `git clone <HTTPS or SSH link>` and that was when the history of the project is being copied from the *remote* server in to your *local* machine.

The advantage of Distributed Version Control Systems that Git uses is that all of the team members have their own *full* history of the project. If the server dies, or lost the project's history, any of the member local project can be copied back to the server without any lost. 

### Work on the local space
Next step, let's add a new file into the project. On this current directory add a new file called `README2.md`. Under that file, just simple type you name into the file. Now go to `terminal` and type `git status` and you will see the following.

![untracked-file](https://user-images.githubusercontent.com/11821799/51422310-00684080-1bdf-11e9-8285-59fdedd4425e.png)

#### Untracked File

Since `README2.md` is newly created, for sure, Git will not see it in the latest snapshot history of the project so Git puts `README2.md` into untracked state.

Next step, run the following command
```sh
# run this first
git add README2.md

# then run this
git status
```

You will see the following lines shows up on your terminal.

![staged-new-file](https://user-images.githubusercontent.com/11821799/51422528-af5a4b80-1be2-11e9-8f68-2d474131a242.png)

Those lines on the image above are saying that now `README2.md` is now being tracked by Git and now it is waiting in the `staging` area (we will talk about `stage` later in this workshop). To prove that Git has already begun its tracking on `README2.md` let's add a second line into the file. And then, type `git state` command.

