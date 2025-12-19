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
##################################################################################################################################################
Task 4: Collaboration and Pull Requests
Now that your feature is complete on its own branch, you need to get it reviewed and merged into the main codebase. This is done through a Pull Request (PR).
Step-by-step instructions:
1.	Go to your Git hosting service (e.g., GitHub): After pushing your branch, the hosting service will often show a notification to create a new pull request. If not, navigate to the "Pull Requests" or "Merge Requests" tab.
 
2.	Create a new Pull Request:
o	Select your feature branch (feature/your-feature-name) as the "source" or "compare" branch.
o	Select the develop branch as the "target" or "base" branch.
o	Provide a clear and descriptive title for your PR (e.g., "new file f1.txt added").
o	Write a detailed description explaining the changes you made, why they were needed, and what a reviewer should look for.
 
3.	Request a code review:
o	Assign the PR to one or more teammates for a code review.
o	Collaborate with your teammates, addressing any comments or suggestions they have by making new commits to your feature branch.
o	Once the reviewers approve your changes, the PR can be merged.

4.	Merge the Pull Request:
o	Once the code is approved and passes all necessary checks (like CI tests), an authorized person can click the "Merge" button.
o	This will merge your feature branch's changes into the develop branch.
o	After the merge, you can safely delete the feature branch both locally and on the remote.
 
