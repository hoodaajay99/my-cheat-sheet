# Download specific tree from a reposotory on Github
```
curl https://codeload.github.com/<username>/repo-name/tar.gz/master 
| tar -xz --strip=<nested-level-of-target-source> <path-to-target-source>
```
- `--strip` = Nested Level number of target source directories

#### Example:

```
curl https://codeload.github.com/hoodaajay99/c_programming_course/tar.gz/master | tar -xz --strip=1 c_programming_course-master

curl https://codeload.github.com/hoodaajay99/c_programming_course/tar.gz/master | tar -xz --strip=2 c_programming_course-master/00-welcome
```
# Automate git push (Not specify username and password) - Over HTTPS

## Use Storage as `credential.helper`

```
$ git config credential.helper store
$ git push http://example.com/repo.git
Username: <type your username>
Password: <type your password>

[several days later]
$ git push http://example.com/repo.git
[your credentials are used automatically]
```
> credentials stored here `$ cat ~/.git-credentials`

Reference - `https://git-scm.com/docs/git-credential-store`


## Use Cache as `credential.helper`

```
$ git config credential.helper cache
$ git push http://example.com/repo.git
Username: <type your username>
Password: <type your password>

[work for 5 more minutes]
$ git push http://example.com/repo.git
[your credentials are used automatically]
```

Flush Cache:
```
$ git credential-cache exit
```
Auto Flush After 300 secs

```
$ git config credential.helper 'cache --timeout=300'
```

> credentials stored in Memory

Reference - `https://git-scm.com/docs/git-credential-cache`


# Automate git push (Not specify username and password) - Over SSH

## Generate an SSH key

### Linux/Mac

```
cd ~                 #Your home directory
ssh-keygen -t rsa    #Press enter for all values
```

### For Windows

- Use Putty Gen to generate a key
- Export the key as an open SSH key

## Associate the SSH key with the remote repository

- Copy the contents of your `~/.ssh/id_rsa.pub`
- Go to settings on Github and click `add SSH key`.
- Paste the key into the field labeled `Key`.

## Set your remote URL to a form that supports SSH 1

- Check your remote URL
```
$ git remote -v
origin	https://github.com/hoodaajay99/my-cheat-sheet.git (fetch)
origin	https://github.com/hoodaajay99/my-cheat-sheet.git (push)
```

Change to form `git+ssh://git@github.com/username/reponame.git`

```
git remote set-url origin git+ssh://git@github.com/hoodaajay99/my-cheat-sheet.git

```

Verify 

```
$ git remote -v
origin  git+ssh://git@github.com/hoodaajay99/my-cheat-sheet.git (fetch)
origin  git+ssh://git@github.com/hoodaajay99/my-cheat-sheet.git (push)
```

## Checkin your changes in your local git repo
```
$ git stage <files>
$ git commit -m "commit message"
```

## Push your changes to remote git / github

```
$ git push
Counting objects: 5, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (5/5), 818 bytes | 0 bytes/s, done.
Total 5 (delta 0), reused 0 (delta 0)
To git+ssh://github.com/hoodaajay99/my-cheat-sheet.git
 * [new branch]      master -> master
 ```



