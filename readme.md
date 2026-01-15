# Gitlab Setup Guide line

## Set up for by default (means one ssh and one git)

### Prepared Machine.
1.prerequisite
```
git --version
```
1.2 git install 
```
sudo apt install git -y
```
2. Configure User
   ```
   git config --global user.name "enter you name"
   git config --global user.email "enter you emai"
   ```
### keep in mind
```
This name and email are not related to GitHub or GitLab authentication.
They are used only as the commit author information.
❌ do not log you in

❌ do not decide which account you push to

❌ do not check against GitHub/GitLab accounts

✅ are written inside each commit object
Author: Name <email>
Committer: Name <email>
```
