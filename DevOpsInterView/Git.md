# Git

- **What is Distributed Version Control System**
  - A DVCS is a method of tracking changes in software files where every developer's local computer storage a complete, mirrored copy of the entire project repository, includes its full history.

- **Explain git clone vs git fork**
  - _git clone_ : Git clone is actually git command that copies a repository to your local computer.
  - _git fork_ : Git fork is actually a web platform feature that copies a repo server-side into your own cloud

- **What is the difference between git pull and git fetch?**
  - git pull : Download new data and instantly merges it.Your working files stay exactly the same.
  - git fetch : Download new data from a remote repo. Modify local files to reflect the remote state.

- **How do you undo the last commit? (git reset/git revert). Difference between ’git reset –soft’, ’–mixed’, and ’–hard’.**
  - (_git reset --soft HEAD~1_) : If you have not pushed your commit to a shared remove server, Git reset alters history by moving your current branch pointer back to the prev
  - (_git reset --mixed HEAD~1_) : This is the default setting applied if you run git reset without explicit modifiers. It removes the commit and un-stages your code changes.
  - (_git reset --hard HEAD~1_) : This complete removes your commits, removed files from staging queue.
