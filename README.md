# How to Open and Save
In order to open the Map, use the Starcraft 2 Editor. Then go to Alcyone_Frontlines folder and find .SC2Map, it is saved as a SC2Components, which looks like a folder in the explorer.
When saving the project, make sure that it is saved with a SC2Components.

## setting up a workplace. 
https://sc2mapster.github.io/mkdocs/setup/

This is a good tutorial to follow. 
however visual studio code is not a must to use.

## Triggers
This is where i need to cleanup a bit, its a bit of a mess at the moment and needs to be sorted into folders. I have also used this to deal with the damage increase per level on abilities. 

--------------
# Git workflow and working on a change
  Never do your work on the master branch. Instead work on a feature branch devoted to what you want to do (see Branch naming above).
  When you're ready to commit something, you rebase onto the master branch, adding your work onto the very tip of the master branch as if it were a single patch you were applying.
## Here's the approach you should use:
  git checkout master # checkout the master branch
  git pull --rebase # get the latest version from remote
  git checkout -b feature/my-feature # checkout new feature branch
## ... do your work here... make commits locally, test your code ...
  git push origin feature/my-feature
  create a Pull request in Github. 
  Send Pull request to someone to review.
## delete branch locally
  git branch -d localBranchName
