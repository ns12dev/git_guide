

  
  

## Git - No panic guide

 
**Clone repository from ssh:gitbox**                               
*You should be assigned to the project, ask for r-w permission to your employer*

Check if you have the permission, then clone the project.
````
ssh gitbox

git clone gitbox:/.../your_project/...
````
----

**Create your personal branch from intermedio**                            
*If present otherwise create your branch and intermedio starting from master/main*

  
````
git fetch

git checkout sviluppo_intermedio

git checkout -b your_branch

````
----

**Check for updates**                                               
*NB if you have uncommitted files push on your branch or stash it*


Check if there are updates on intermedio.
````
git fetch 
````
Pull & Resolve conflicts if present.
````
git pull origin sviluppo_intermedio
````
Push the updates on your branch.
````
git push origin your_branch
  ````

----
  

**Push all files on your branch**
````
git add *

git commit -m "commit"

git push origin your_branch
````

----
  

**Push all files on intermediate branch**

````
git add *

git commit -m "commit"

git push origin your_branch
````
Check if there are some updates, in this case pull, then push and merge update on your branch resolving eventually conflicts.
````
git fetch

git pull origin intermediate_branch

git push origin your_branch
````
Then checkout to the intermediate branch, pull the merged updates of your branch (should be conflict-free at this point) then push on intermedio and ***back to your branch.***
````
git checkout intermediate_branch 

git pull origin your_branch 

git push origin intermediate_branch 

git checkout your_branch
 ````

----

  

**Put current development on stash**  
*Useful when you want to get new updates without push on your branch, maybe for WIP/test code*
<br>
````
git stash
````
 
**Retrive file from stash**

  ````
  git stash apply
````


  

  

## The following are for personal sake/development

**Git global setup**  
*Already configured in NS12*
````
git config --global user.name "your-username"

git config --global user.email "your-mail@email.com"
````
  
----

  

**Create a new repository**  
*for personal development, in NS12 ask it to your employer.*
<br>
````
git clone https://gitlab.com/.../repo.git

cd repo

touch README.md

git add README.md

git commit -m "add README"

git push origin main

````

----

  

**Push an existing Git repository**
````
cd existing_repo

git remote rename origin old-origin

git remote add origin https://gitlab.com/.../repo.git

git push origin --all

git push origin --tags
````
