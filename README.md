# best-repo-ever
Trailhead Git and GitHub Basics-Work with the GitHub Workflow 
Track a File with GitHub
Now that you have a local copy of the repository and you have configured Git, you’re ready to use the GitHub Workflow to make some changes to the project. Let’s start by making a simple change to the README.md file. 

Step 1: Create a Branch
To see a list of local branches, type git branch. Right now, you probably only see one branch: master. 

Let’s create a new branch (myfeaturebranch) for our work:

Type git branch myfeaturebranch
Checkout to that branch: git checkout myfeaturebranch
You should see something like this:

1
kjameson-ltm:best-repo-ever kjameson$ git branch
2
   * master 
3
kjameson-ltm:best-repo-ever kjameson$ git branch myfeaturebranch
4
kjameson-ltm:best-repo-ever kjameson$ git checkout myfeaturebranch
5
  Switched to branch 'myfeaturebranch'
Note: If you’ve heard of checkout from other VCS, it likely means something different than in Git. With Git, checkout moves an important pointer called HEAD, and in this case, moves us to a different branch. HEAD points to the tip of your branch. We talk more about HEAD in our last unit. 

Step 2: Make Changes to README.md File and Commit the Change to Your Local Repository
Now that you’ve checked out to the new branch, well make some changes and see Git in action.

Open the README.md in your repository
Add some content using your favorite text editor.
When you’re finished, save your changes.
After you made some changes to your file, it’s time to create your first snapshot. When working from the command line, you will need to be familiar with the idea of the two stage commit.

When you work locally, your files exist in one of four states. They are either untracked, modified, staged, or committed. Git tracks these files, and keeps track of your history by organizing your files and changes in three trees. They are working, staging (also called index), and history. When we add, delete, and make changes to files, we do this in the working tree.

Diagram of the three trees of Git, working, staging, and history.

To add your changes to version control, create a collection of files that represent a discrete unit of work—we build this unit in the staging area.

When we are satisfied with the unit of work we’ve assembled, we take a snapshot of everything in the staging area. This is called a commit.

Let’s complete the process using the commands git add and git commit: 

Check the status of our working tree: git status
1
kjameson-ltm:best-repo-ever kjameson$ git status
2
On branch myfeaturebranch
3
Changes not staged for commit: 
4
      (use "git add <file>..." to update what will be committed) 
5
      (use "git checkout -- <file>..." to discard changes in working directory)  
6
   modified: README.md
7
no changes added to commit (use "git add" and/or "git commit -a")
Move the file from the working tree to the staging area: git add README.md
Enter git status to see what happened:
1
kjameson-ltm:best-repo-ever kjameson$ git status
2
On branch myfeaturebranch
3
Changes to be committed:
4
      (use "git reset HEAD <file>..." to unstage)
5
   modified: README.md
Take our first snapshot: git commit -m “My first commit”
Let’s take another look at our repository status: git status
1
kjameson-ltm:best-repo-ever kjameson$ git status
2
On branch myfeaturebranch
3
nothing to commit, working tree clean
Step 3: Send Changes to the Remote Repository
Right now, this commit is only local. If you check the remote repository, you won’t see your branch or the changes you just made. To see the changes on the remote, you first need to push your changes to the remote repository. 

Since we created this branch locally, we’ll first create a remote branch that matches our local one. With the same command, we’ll also set up a tracking relationship between the two branches.

Type git push -u origin myfeaturebranch
When asked, enter your GitHub username and then your password.
01
kjameson-ltm:best-repo-ever kjameson$ git push -u origin myfeaturebranch
02
Username for 'https://github.com': kierenjameson 
03
Password for 'https://kierenjameson@github.com': 
04
Counting objects: 6, done.
05
Delta compression using up to 4 threads. 
06
Compressing objects: 100% (4/4), done.
07
Writing objects: 100% (6/6), 551 bytes | 0 bytes/s, done. 
08
Total 6 (delta 1), reused 0 (delta 0) 
09
remote: Resolving deltas: 100% (1/1), done.
10
To https://github.com/kierenjameson/best-repo-ever.git
11
   * [new branch] myfeaturebranch -> myfeaturebranch 
12
Branch myfeaturebranch set up to track remote branch myfeaturebranch from origin.
Note:  You only need this long command the first time you push a new branch. After that, you can simply type git push.

Step 4: Create a Pull Request
Now that you’ve pushed your changes to your remote repository, let’s open a pull request on GitHub. 

Go to your GitHub account on the web
Click the Pull Request tab
Click New Pull Request
In the Base dropdown, choose master
In the Compare dropdown, choose myfeaturebranch. You should see something like this:
Screenshot from GitHub showing comparison of changes between master branch and myfeaturebranch.

Click Create pull request
Enter a Subject line and Comment
Click Create pull request
Control Code Quality with Code Review
Pull requests are more than just a comparison of branches, they’re a way to review code and ensure quality, through both human and automated efforts.

General Conversation 
Use the Conversation tab to add general comments on a pull request.

Line Comments 
In the Files Changed tab (A), can hover over a line to see a blue + icon (B). Clicking this icon will allow you to enter a comment (C) on a specific line. These line level comments are a great way to give additional context on recommended changes. They will also be displayed in the conversation view.

Screenshot showing how to add line comments.

Review 
When you are making line comments, you can also choose to Start a Review (D). When you create a review, you can group many line comments together with a summary message. When you submit the review, you can indicate whether it is just a comment, an approval, or a request for changes. Pull request reviews have special power in GitHub when used in conjunction with protected branches, you can prevent a pull request from being merged if it has not had at least one review. 
Automated Tests 
If you’ve integrated CI/CD with your project, you will see the status of your tests reported right on the pull request. These tests are highly customizable. 
Merge Your Changes
When you merge your branch, you take the content and history from your feature branch and add it to the content and history of the master branch.

Merging is quick and easy—click Merge pull request, add a merge comment, and click Confirm merge.

Your team should establish rules about who should merge a pull request. Some options include:

The person who created the pull request should merge, as they’ll need to resolve issues resulting from the merge.
Assign a single person within the project team. This ensures consistency but can become a bottleneck.
Anyone other than the person who created the pull request can merge. This ensures at least one review has taken place.
Keeping It All in Sync
After you merge your pull request, delete the branch on GitHub. To do this click Delete branch at the bottom of the pull request screen.

However, merging and deleting on GitHub will not automatically update your local copy of the repository. Let’s go back to our command line application and get everything in sync.

First, we need to get the changes we made on GitHub into our local copy of the repository:

Switch back to your default branch: git checkout master
Retrieve all of the changes from GitHub: git pull
01
kjameson-ltm:best-repo-ever kjameson$ git checkout master
02
Switched to branch 'master'
03
Your branch is up-to-date with 'origin/master'.
04
 
05
kjameson-ltm:best-repo-ever kjameson$ git pull
06
remote: Counting objects: 1, done.
07
remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
08
Unpacking objects: 100% (1/1), done.
09
From https://github.com/kierenjameson/best-repo-ever 
10
       f464053..599f35f master -> origin/master
11
Updating f464053..599f35f
12
Fast-forward
13
   README.md | 4 +++- 1
14
   file changed, 3 insertions(+), 1 deletion(-)
Note:  git pull is a combination command that retrieves all of the changes from GitHub and then updates the branch you’re currently on, to include the changes from the remote. The two separate commands being run are git fetch and git merge.

Quiz Challenge +100 points

1 What is the first step of the GitHub flow?
A
Merging
B
Committing
C
Branching
D
Cloning
2 Which of the following commands is used to synchronize the remote and local working environments?
A
git pull
B
git merge
C
git status
D
git commit
3 What command moves a file from the working directory to the staging area?
A
git status
B
git remote -v
C
git staging
D
git add