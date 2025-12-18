Task 1 & Task 2:

Step 1: I had forked the git repository https://github.com/jsachdev07/DevOpsClassCodes.git
Step 2: Added New README.md file
#############################################################################
Task 3: Branching Strategy

The scenario states your team uses the GitFlow branching strategy. This strategy is a structured approach to managing your codebase.
Step-by-step instructions:
1.	Ensure you are on the d branch: The Git Flow model uses a main develop branch for all feature integration. Before you start, make sure your local repository is up-to-date with the remote develop branch.
	First, switch to the develop branch: git checkout master.
  Then, pull the latest changes from the remote: git pull origin master.
2.	Create a new feature branch: All new work is done on a dedicated feature branch to keep it isolated from the main codebase. According to GitFlow, these branches are typically named feature.
o	Create and switch to your new branch with one command: git checkout -b feature.

3.	Start coding and committing: Now you can begin working on the new feature. Make changes to the files and commit your work regularly.
•	After making changes, add the files to the staging area: git add .
•	Commit the changes with a clear message: git commit -m "f1.txt file added".

4.	Push your feature branch to the remote repository: To share your work with your team, you'll need to push your feature branch to the remote repository.
•	Use the command: git push -u origin feature.
This sets up your local branch to track the remote branch.





