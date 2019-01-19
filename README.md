# SOURCE CONTROL HANDS ON WORKSHOP

## Table of content

* [Slide](#Slide)
* [Overall Git's structure](#Overall-Git's-structure)
* [Remote VS Local](#Remote-VS-Local)
* [Untracked files](#Untracked-Files)
* [Tracked Files](#Tracked-Files)

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

#### Untracked Files

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

![change-to-stage-file](https://user-images.githubusercontent.com/11821799/51422588-c0578c80-1be3-11e9-868a-b47fa534ee19.png)

Notice that Git knows about the new change that was added to `README2.md`. However, it does not put `README2.md` into untracked section like it did when we first added the file with our name on the first line.

#### Tracked Files
Opposite to untracked files, tracked files are the files that Git knows from the latest snapshot history. Tracked files can be presented in 3 different types.

* Unmodified
* Modified
* *Staged*

You may notice that `Stage` part above is *italic* and seem different than `Unmodified` and `Modified` bullets. Let's make them all looks identical by removing ` *...* ` that right now surrounding the text of the last bullet. After you do so, again, run `git status` command on your terminal. 

![Modified-readme](https://user-images.githubusercontent.com/11821799/51426458-d124f400-1c1d-11e9-89c3-267d6b2a6521.png)

You should see that now you have changed the state of `README.md` from `Unmodified` to `Modified`.

To stage tracked files, we use the same command as untracked files. Can you guess what it is ? Let's do it !

##### Files life cycle summary
![file-life-cycle](https://user-images.githubusercontent.com/11821799/51426727-375f4600-1c21-11e9-82f2-f95112e20cd1.png)

#### Ready to commit
Committing means saving the files changes that are in staging area into the projects history. We usually do it when we have finished a logical unit of works. Let's say when I finish writing down this section, I would stage `README.md` into the staging area. Then make a commit with some useful message like `Finished Ready to commit section`.

##### Staging area
Most of the time, in the real code base you might have modified 10 files in the first 2 hours of work. However, only the first three files are related to `Date calculation logic` of your application. This is where `staging area` comes in handy. You can use `git add <PATH>` with the 3 selected files to separate them into staging area away from the other non-related (by logical responsible). Then you can make a commit that contains just only the files you picked that reside in the staging area.

On the previous section you remove ` *...* ` away from the last bullet of *tracked files* section. And then added `README.md` into the staging area. Now let's use `git commit` command to make your first commit !

```sh
# type the following command into your terminal
git commit -m "remove italic from the last bullet of tracked files section"
```

And that was done, your first commit ! 
 

