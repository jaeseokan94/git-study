# git_study
learning git with Pro git by Scott Chacon and Ben Straub 

Summary of Pro Git by Scott Chacon and Ben Straub 


Chapter 1 

Version Control 
Records changes to a files over time so that you can recall specific versions later. 
You can easily recover when there’s some problems. 
You can simply do Local control systems which I usually do , however, the problem is you can get easily confused. (e.g. writing in wrong directory.)
There’s a bit better method which is Centralized Version Control Systems, which is save all different versions in one central server. The problem occurs when the server down. There’s a risk of losing everything. 
Finally, Git is called “Distributed Version Control Systems”. Every individual will have their own repository, and all the versions will be saved in each repository. 

Git
Git saves every versions in local, therefore almost no time is taken to retrieve past version. 
Git stores it’s data into SHA-1 hash. Every changes will be recorded in Git. 


Committed , Modified , Staged 
Committed means data is stored in your local database. (Repository) 
Modified means data is changed but not committed. (Working directory)
Staged means you have makred a modified file in its current versions to go in to next commit.  (Staging directory) 

Basically, you work on files, and then modify it, and then commit it. 
Working directory to staging area to repository. 



Following is my Git status : user.name=jaeseok an
user.email=k1462487@kcl.ac.uk


Chapter 2 

In order to track existing project on Git, go to project’s directory 

Git - version control , Create first version

Git clone [url] [filename u want to create]

Git status -> It shows 1.what branch you are in 2. changed status of files. 

For example, 

anjaeseogs-Air:projecteuler JAESEOKAN$ git status
On branch master
Your branch is up-to-date with 'origin/master'.

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   Problem12.java
	modified:   Problem16.java
	modified:   problem3.java
	modified:   problem7.java
	deleted:    project_euler

no changes added to commit (use "git add" and/or "git commit -a")

Git status -s -> will show following 

anjaeseogs-Air:projecteuler JAESEOKAN$ git status -s
 M Problem12.java
 M Problem16.java
 M problem3.java
 M problem7.java
 D project_euler


 
cat .gitignore  -> will make git files to not appear in Git status 

git diff -> will show git files which has been changed but not pushed. 

anjaeseogs-Air:projecteuler JAESEOKAN$ git diff
diff --git a/Problem12.java b/Problem12.java
index 522a95f..3b8c4cd 100644
--- a/Problem12.java
+++ b/Problem12.java
@@ -1,6 +1,8 @@
+
 package projectEuler;
 
 public class Problem12 {
+       
        public static void main(String[] args) {
                long num,i,j,count;
                num=0;
@@ -20,7 +22,6 @@ public class Problem12 {
        } 
                long estimatedTime = System.nanoTime() - startTime;
         System.out.println(estimatedTime/1000);
-        System.out.println("done");
        }       
 }
 //57177120
diff --git a/Problem16.java b/Problem16.java
index 4bcf7dd..350fdfb 100644
:

git rm --cached (filename) : When you made change in file, but you don’t want to upload that change on git. 

git rm \*~ : It will remove all files that end with ~. 

git mv file_from file_to : move file 
git mv README.md README
git status 

is equal to 

mv READ.md README
git rm README.md
git add README

git log : will show your commit history 


When you have a message like:
"Your branch and 'origin/master' have diverged, # and have 1 and 1 different commit(s) each, respectively."

, check if you need to update origin.

If origin is up-to-date, then some commits have been pushed to origin from another repo while you made your own commits locally.

    ... o ---- o ---- A ---- B origin/master (upstream work) \ C master (your work)
You based commit C on commit A because that was the latest work you had fetched from upstream at the time.
However, before you tried to push back to origin someone else pushed commit B.
Development history has diverged into separate paths. 
You can then merge or rebase. See Pro Git: Git Branching - Rebasing for details.

Merge
Use the git merge command:

    $ git merge origin/master
    
This tells Git to integrate the changes from origin/master into your work and create a merge commit.
The graph of history now looks like this: 

    ... o ---- o ---- A ---- B origin/master (upstream work) \ \ C ---- M master (your work)
    
The new merge commit M has two parents, each representing one path of development that led to the content stored in the commit.
Note that the history behind M is now non-linear.
Rebase
Use the git rebase command:

    $ git rebase origin/master
    
This tells Git to replay commit C (your work) as if you had based it on commit B instead of A.
CVS and Subversion users routinely rebase their local changes on top of upstream work when they update before commit.
Git just adds explicit separation between the commit and rebase steps.
The graph of history now looks like this:

    ... o ---- o ---- A ---- B origin/master (upstream work) \ C' master (your work)
    
Commit C' is a new commit created by the git rebase command.
It is different from C in two ways:
It has a different history: B instead of A.
It's content accounts for changes in both B and C: it is the same as M from the merge example. 
Note that the history behind C' is still linear.
We have chosen (for now) to allow only linear history in cmake.org/cmake.git.
This approach preserves the CVS-based workflow used previously and may ease the transition.
An attempt to push C' into our repository will work (assuming you have permissions and no one has pushed while you were rebasing).

The git pull command provides a shorthand way to fetch from origin and rebase local work on it:

    $ git pull --rebase
    
This combines the above fetch and rebase steps into one command.

    git reset --hard origin/master

This can do
