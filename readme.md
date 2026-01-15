![Architecture Diagram](Untitled-2025-10-20-1802.png)
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
### 3 Generate SSH key 
```
ssh-keygen -t rsa -b 4096 -C "your-email@example.com"
```
If the SSH key has no passphrase, ssh-agent (and eval) is not needed.
If the SSH key has a passphrase, eval "$(ssh-agent -s)" helps by connecting the shell to ssh-agent, so the passphrase is entered once and not repeatedly.

   ### 3.1 if use passphase then use eval
   ```
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_rsa
   ```
   Auto-load via shell and systemd
   ```
   # ~/.bashrc
   eval "$(ssh-agent -s)" >/dev/null
   ssh-add ~/.ssh/id_rsa 2>/dev/null
   using systemctl --user enable ssh-agent
   ```
### 3.2 Not using passphase
```
cat ~/.ssh/id_rsa.pub
```
public key add into Gitlab
```
gitlab -> Profile -> Preferences
SSH keys
Key box paste
add key
ssh -T git@gitlab.com
```
## git colne 
```
git clone git@gitlab.com:username/repo-name.git
```

## Extra command for git
```
git config list
git remote -v
git status
git branch
git switch branch-name
```
## ssh flow
```
git pull
 ↓
SSH connects to vcs.technonext.com ( duiting this phase it read from  /etc/ssh/config or ~/.ssh/config right? )
 ↓
Server matches your public key (profile key)
 ↓
Authenticates you as user: mahbubl.hasan
 ↓
User has read access to repo
 ↓
git pull success
```



   




