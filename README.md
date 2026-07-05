# version-control-simulation-Anjan
Project Setup
This repository was created as part of a version‑control assignment to practice working with Git, GitHub, branching, and local development workflows. The project intentionally began as an empty GitHub repository, with all files created and managed locally.

Initial Setup Steps
Created an empty GitHub repository  
The repo was initialized without a README or starter files, as required by the assignment.

i) Cloned the repository locally
git clone https://github.com/AnjanSripathi/version-control-simulation-Anjan.git
cd version-control-simulation-Anjan
Created project files locally  
All initial files were created and committed from the local environment.

ii) Established proper branch structure  
A main branch was later created and pushed to GitHub to serve as the primary integration branch.

iii)Branch Initialization Issue & Resolution
Issue Summary
Because the repository was created empty, GitHub did not automatically generate a main branch. GitHub only creates main when at least one file (e.g., README) is added during repo creation.

iv) After cloning the empty repo, the first branch I created and pushed was:
feature/header
GitHub interpreted this as the first and only branch, and therefore set:
origin/feature/header as the default branch.
This caused several issues:
1) main did not exist locally or remotely

2) git branch -a showed only feature/header

3) git fetch --all returned no additional branches

4) Switching to main failed because it wasn’t present

v) The remote HEAD pointer showed:
remotes/origin/HEAD -> origin/feature/header
Root Cause :
The repository had no initial commit, so GitHub had no default branch.
The first pushed branch became the default by necessity.

Resolution Steps:
To restore a proper Git workflow:-
1) Created a new main branch locally
git switch -c main

2) Removed the incorrect upstream reference
git branch --unset-upstream

3) Pushed the new main branch to GitHub
git push -u origin main

4) Changed the default branch on GitHub  
GitHub -> Settings -> Branches -> Default branch -> main

5) Refreshed the local HEAD pointer
git remote set-head origin -a

6) After these steps, the repository now correctly contains:
main (default branch)
feature/header (active development branch)
This aligns the project with standard Git workflows and the assignment requirements.

vi) Branching Strategy
This project follows a simple and clean branching model suitable for assignments and small projects.
1) Main Branch (main)
Serves as the default branch.
Contains stable, reviewed, and approved code.
All feature work is merged into main through pull requests.

2) Feature Branches (feature/<name>)
Used for isolated development of specific tasks or components.
Example:
i) feature/header
Created from main:
git checkout main
git checkout -b feature/<name>

ii) Pull Request Workflow
Complete work on the feature branch.

iii) Push changes to GitHub:
git push -u origin feature/<name>

iv) Open a Pull Request targeting main.
Review and merge once approved.

v) How to Contribute
Although this is a solo assignment, the repository is structured to support collaborative workflows.

1. Clone the repository
git clone <repo-url>
2. Create a new feature branch
git checkout main
git checkout -b feature/<task-name>
3. Make changes locally
Add or modify files as needed.
4. Commit your work
git add .
git commit -m "Describe your changes clearly"
5. Push your branch
git push -u origin feature/<task-name>
6. Open a Pull Request
GitHub → Compare & Pull Request → Target main.
7. Merge after review
Once approved, merge the PR into main.
