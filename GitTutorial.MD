# Git Tutorial #
#### This is a tutorial that will cover the basics of using Git from the command line. By the end of this tutorial you will be able to branch, perform stashes, and even merge branches.
---
## **A Breif Overview**
#### Git is essesntially a timeline management utility for projects.
<details open>
<summary>Important Terminology</summary>
<h4>Repositories</h4>
In Git, Repositories are a sort of data structure which store files and directories along with metadata about the changes that those files has undergone. Repositories contain all project data. When a repository has its first comit, its state is saved. This is where you project timeline begins. 
<h4>Branches</h4>
In Git, branching is when you diverege from the main branch when working on a repository. When you start a repository, a main branch is created and is usually where the main working project is being worked on. When you create a branch from the main project, it is usually to add a feature or a fix a bug in the project. 
<h4>Commit</h4>
Commits are the core building block units of a Git project timeline. Commits are snapshots along the timeline of a Git project. They are stored in your local repository.
<h4>Stashes</h4>
When you want to switch branches but your work is not complete in the current branch you are in, you might not want to commit half done work. Stashing on git allows you to save your work and switch branches without commiting the current branch.
<h4>Merging</h4>
Merging in Git is when you combine a working branch back into your main branch. The changes you made in your working branch are implemented into the main branch when you merge if there is no confilicting code.
</details>

---

## **Creating a Git Project**

### Step 1:
### Initialize a new Repository
The first step in initalizing a new Repository is to open up terminal. Once you open up terminal type in the following command:

`git init TestRepo`

Once you have done this, your terminal will say:

`Initialized empty Git repository in /Your Directory/TestRepo/.git/`

You will now want to change your current directory to where the new Repository was created. You can do this by typing:

`cd /PathToProject/TestRepo`


Right now your Repository is empty. If you type `git log` it will say `fatal: your current branch 'master' does not have any commits yet`.
This is because you have not made any commits yet. You will also notice that we are currently on the main branch. 

We will add a text file to our repository to demonstarate dow to add files and commit them. Download[ this file.](https://github.com/eddie-droid/GitTutorial/blob/main/TestFile.txt)
Once you have thee file downloaded moce it into your TestRepo directory. Once it is there you can type `git status` to check the status of your Repository.
You will notice it says:

`On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	TestFile.txt

nothing added to commit but untracked files present (use "git add" to track)`

This is showing that there are now files in your repository but they are not being tracked. In order to start tracking them you must add them and then commit. In order to do this type:


`git add TestFile.txt`

Then you can type:

`git commit -m "First Commit"`

You will then be shown that the commit was succesful. If you type `git log` now you will see your commit.

Now lets say we want to add a feature to our code in our text file. If you open up the text file in an editor you will see it has two functions, an add and subract function. 
If we want to add a function, lets say to multiply and divide, we would probably want to create a new branch to work on these new added functions. 
In order to do this, type `git branch addedFunctions` in your terminal. This will create the new branch called "addedFunctions". Next you will want to type `git checkout addedFunctions`. This will switch you from the master branch to your newly created branch.


Next, open up your text file and add the following text to the end of the file and save:

`
Multiply (x, y):
  return x*y`
  
If you type git status you will notice it detected that the file changed its contents. In order to commit these changes type the same two commands as before:

`git add TestFile.txt`


`git commit -m "Added Multipication Function"`

Now you have a branch that is not in your master branch since you commited while on your `addedFunctions` branch. 

Now lets say you start working on your divide function but you did not finish it and you want to switch back to your master branch. You don't want to use a commit on code that is not complete. What you might want to do in this situation is stash your changes. 
In order to see how to do this, add the following code to the end of your text file and save:

`
Divide (x, y):`

After doing this, in your terminal type `git stash save "Start of Divide Function"`. If you go back to your TestFile.txt you will notice tha the changes you made to the file of adding a divide function are gone. They have been stashed in Git. Now you can safely branch to the master branch using `git checkout master` without losing your work. Now let us go back to our `addedFunctions` branch using `git checkout addedFunctions`

If we want to restore our stashed work, type:

`git stash pop`

Now you will notice our added divide function is restored. To complete the function let us add the following to the end of our text file and save:

`  return x/y`

Now let us add and commmit our final changes to our addedFunctions branch.

`git add TestFile.txt`


`git commit -m "Added Divide Function"`

Now that we have finished adding the functions we wanted to in our addedFunctions brancb, we want to combine our additional code back to our master branch code. We can do this by merging the two branches back into the master branch. 
We can do this by typing the following commands:

`git checkout master`

then

`git merge addedFunctions`

You have successfully merged your branches and are back in your master branch. The last step you might want to take is deleting the addedFunctions branch since you have no use for it anymore. You can do this using the following command:

`git branch -d addedFunctions`

## Congratulations 🎉
### You have reached the end of this tutorial. Now you know how to branch, stash, and merge. Hopefully you feel comfortable using git now. Goodluck.
