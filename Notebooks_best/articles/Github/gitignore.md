---
created: 2023-03-18T20:54:04 (UTC +01:00)
tags: [
    -clipped
    -github
    -newRepo
    -newNotebook
    -Notebook
    -(.gitignore)
    ]
source: https://stackoverflow.com/questions/10176875/add-gitignore-to-gitignore/10728244
author: user1125394user1125394
---

# git - Add .gitignore to gitignore - Stack Overflow

> ## Excerpt
> Is it possible to add the .gitignore file to .gitignore itself?

.gitignore
Doesn't work though

I don't want to see it in edited files

---
A .gitignore can ignore itself _if it's never been checked in:_


mhaase@ubuntu:~$
`git --version`
`git version 1.7.9.5`
mhaase@ubuntu:~$ 
`git init temp`
`Initialized empty Git repository in /home/mhaase/temp/.git/`
mhaase@ubuntu:~$ 
`cd temp`
mhaase@ubuntu:~/temp$ 
`touch .gitignore foo bar baz bat`



mhaase@ubuntu:~/temp$ 
`git status`
```
# On branch master
#
# Initial commit
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#       .gitignore
#       bar
#       bat
#       baz
#       foo
```


mhaase@ubuntu:~/temp$ 
```echo "foo" >> .gitignore```
mhaase@ubuntu:~/temp$ 
```echo ".gitignore" >> .gitignore```
mhaase@ubuntu:~/temp$ 
```git status```
```
# On branch master
#
# Initial commit
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#       bar
#       bat
#       baz
```
nothing added to commit but untracked files present (use "git add" to track)


If you check in .gitignore (before you tell it to ignore itself), then it will always show up in git status, even if you later modify it to ignore itself.


---------------------------------------------------------

Mark E. Haase

>Exactly, this is my case. I want to have a local .gitignore for working with git-svn, which no-one should see. So I just added it to itself and it just worked. But then I googled to see if some uptight people will explain to others how this is "bad". This answer should be accepted, and then I would upvote the .git/info/exclude suggestions also. So it just needs to be untracked... Not very surprising, at least if you've ever been "subverted" (svn). – 

Tomasz Gandor
> I have .gitignore file got backup first. Then I use git rm .gitignore and commit that change. At last, add and commit .gitignore file again with rule for .gitignore. It works! – 

qzhang
> To fix this you can run git rm --cached .gitignore. – 

Gideon
> Makes perfect sense. .gitignore ignores untracked files. If the .gitignore file itself is untracked, it can ignore itself too. Yes, this violates the original purpose of .gitignore but that doesn't mean it can't be used this way. – 

ADTC
>There's not really a good reason to do this. If you want files ignored for your clone only, add them to .git/info/exclude, not in .gitignore file.




# On branch master
#
# Initial commit
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#       .gitignore
#       bar
#       bat
#       baz
#       foo
> mhaase@ubuntu:~/temp$ echo "foo" >> .gitignore
> mhaase@ubuntu:~/temp$ echo ".gitignore" >> .gitignore
> mhaase@ubuntu:~/temp$ git status
# On branch master
#
# Initial commit
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#       bar
#       bat
#       baz

