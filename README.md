# GIT-35 – Merge Conflict Resolution

cd "GIT-35" – moved into my project folder
git init – turned the folder into a git repo
git status – checked nothing was tracked yet

git config user.email "annujjguptaa@gmail.com" – set my email so commits are tagged to me
git add . – staged README.md and greeting.txt
git commit -m "Initial commit" – first commit, just "Hello World" in greeting.txt
git branch -M main – renamed the default branch to main

git checkout -b feature-branch – made a new branch to edit the file separately
git add greeting.txt – staged the edited file (rewrote it as an intro for "Anuj Gupta")
git commit -m "Update greeting in feature-branch" – committed that version on feature-branch

git checkout main – switched back to main
git add greeting.txt – staged main's version of the same file (rewrote it as "Vidhrit" instead)
git commit -m "Update greeting in main" – committed that version on main

git merge feature-branch – tried merging feature-branch into main

## The conflict
Both branches had changed the exact same line of greeting.txt, just to different text (main had the Vidhrit intro, feature-branch had the Anuj Gupta one), so git couldn't auto-merge it and threw a conflict on greeting.txt. Running git status showed it listed under "both modified". Opening the file showed git's conflict markers right inside it – <<<<<<< HEAD, then main's version, then =======, then feature-branch's version, then >>>>>>> feature-branch.

## How I fixed it
I opened greeting.txt in VS Code and deleted the marker lines by hand, then decided to just keep both intros instead of picking one – so the file now has the Vidhrit line followed by the Anuj Gupta lines. After that:

git add greeting.txt – marked the conflict as resolved
git commit -m "Resolve merge conflict in greeting.txt" – finished the merge with a commit

git log --oneline --graph --all – checked the history after, shows main and feature-branch splitting off and then joining back at the merge commit

git remote add origin https://github.com/annujjguptaa-cpu/GIT-35.git – linked the repo to GitHub
git push -u origin main – pushed everything up

## Result
greeting.txt has both introductions in it now, no conflict markers left, and the commit graph shows the full branch → edit → merge path clearly.

Repo: https://github.com/annujjguptaa-cpu/GIT-35
