# GIT-35 - Merge Conflict Resolution

## Objective
This repository was created to deliberately trigger a merge conflict in Git
and document, step by step, how it was resolved.

## Tools Used
- Windows PowerShell (all git commands were run here, no other terminal)
- VS Code (used only to edit greeting.txt between git commands)
- Git and GitHub

## Steps and Commands

### 1. Initialise the repository
cd "GIT-35"
git init
git status

### 2. Configure identity and make the first commit
git config user.email "annujjguptaa@gmail.com"
git add .
git commit -m "Initial commit"
git branch -M main

### 3. Create feature-branch and edit greeting.txt
git checkout -b feature-branch
git add greeting.txt
git commit -m "Update greeting in feature-branch"

### 4. Switch to main and edit the same line differently
git checkout main
git add greeting.txt
git commit -m "Update greeting in main"

### 5. Merge and trigger the conflict
git merge feature-branch
git status

## The Conflict
main had changed the first line of greeting.txt to a Vidhrit introduction,
while feature-branch had changed the same line to an Anuj Gupta introduction.
Git could not auto-merge these and inserted conflict markers
(<<<<<<< HEAD, =======, >>>>>>> feature-branch) directly into greeting.txt.

## Resolution
The conflict markers were removed manually in VS Code and both introductions
were kept, one after the other, instead of discarding either version.
git add greeting.txt
git commit -m "Resolve merge conflict in greeting.txt"

### 6. Verify history
git log --oneline --graph --all

### 7. Push to GitHub
git remote add origin https://github.com/annujjguptaa-cpu/GIT-35.git
git push -u origin main

## Final Result
greeting.txt now contains both introductions with no conflict markers left,
and the commit graph shows main and feature-branch diverging and then
joining back together at the merge commit.

Repository: https://github.com/annujjguptaa-cpu/GIT-35
