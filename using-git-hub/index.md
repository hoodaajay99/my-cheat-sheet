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



