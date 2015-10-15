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