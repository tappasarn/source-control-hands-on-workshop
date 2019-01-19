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

