# Automate git push (Not specify username and password)

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

## Checkin and Push your changes

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



