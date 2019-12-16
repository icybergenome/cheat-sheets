# Basic Git Commands #
Purpose |	Command |	Args |	Notes
--------|---------|----|-------------------------
 Clones a repository into a newly created directory| git-clone | -l, -s etc | URL: https://git-scm.com/docs/git-clone 
Initialize Project|	git init |		
Status of Project|	git status|		
Add files/ Add Changes|	git add|	<FileName>, -A (add All files in dir), “.” to add all untracked files |
Commit|	git commit 	|-m “Message for Commit” |
List All Commits |	git log |		
Point to particular commit |	git commit 	| <First 7 letters of commit id> |
Current branch |	git branch |		
New Branch |	git checkout |	-b **BranchName** | If Head is pointing to a particular commit, that commit will be committed to newly created branch.
Link to new Remote Directory |	git remote |	add origin <ssh of remote dir> |
List Remote Dirs |	git remote	| -v |
Pull from git |	git pull origin	| <BranchName>	|
Untracked files check before remove	| git clean -n |		
Remove Untracked files |	git clean -f | 	-d to remove directories	|
Fetch files | git fetch | put --all to fetch all files | 
Stash the changes in a dirty working directory away|  git-stash  | pop, apply, branch etc |URL: https://git-scm.com/docs/git-stash
Reapply commits on top of another base tip | git-rebase | [-i , --interactive] | URL: https://git-scm.com/docs/git-rebase
Reset current HEAD to the specified state | git reset | [mode] [commit] | URL: https://git-scm.com/docs/git-reset
Show changes between commits, commit and working tree, etc | git diff | -p, -u etc | URL: https://git-scm.com/docs/git-diff
Remove files from the working tree and from the index | git-rm | -f, --force etc | URL: https://git-scm.com/docs/git-rm
Create, list, delete or verify a tag object signed with GPG | git tag | -a, -s etc | URL: https://git-scm.com/docs/git-tag

## Git Flow commands and installation ##
<https://danielkummer.github.io/git-flow-cheatsheet/>
### Installation ### 	
**$ brew install git-flow-avh** ***or***	**SourceTree**

Purpose | Command | Alternative | Details
--------|---------|-------------|----------------|
Initialization (existing GIT dir) |	git flow init | | |		
Start Feature |	git flow feature start MYFEATURE | | |		
Push to Server(Github) |	git flow feature publish MYFEATURE |	git push origin feature/MYFEATURE | |
From GUI create Pull Request | | |			
Finish the Feature |	git flow feature finish MYFEATURE | |	Merges MYFEATURE into 'develop'|
 | | | Removes the feature branch |
 | | | Switches back to 'develop' branch |
Push to Server(Github) |	git push origin develop	| | |
Delete feature branch from GUI(optional) | | |			
