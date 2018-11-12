# BATO
Bridgestone Americas Tire Operations - Presentation and technical source


## Documentation
- [Presentation layer](presentation-source/README.md)
- AEM




## Using Git
This project uses Git with gitflow

0. Fork repo from `https://github.com/Razorfish-East/BATO`

- Clone your newly created fork
```
git clone https://github.com/[username]/BATO
```

- Your clone will automatically set a remote to `origin`
- We now need to add a new remote repo to Razorfish
```
git remote add upstream git@github.com:Razorfish-East/BATO.git
```

---
### Gitflow
Now you will have everything you need to start installing `git flow`. For more information visit [A successful Git branching model](http://nvie.com/posts/a-successful-git-branching-model/) or [Getting started](http://yakiloo.com/getting-started-git-flow/)


#### Install

**OSX**

- The easiest way to install it, is to use brew
```
brew install git-flow
```

**Windows**

- Use [SoureTree](http://www.sourcetreeapp.com/)

#### Init gitflow
Change directory into the project folder

```
git flow init
```


#### Creating a feature branch

0. To start on a new feature
```
git checkout master
```
```
git pull --rebase upstream master
```
Start a new feature based on the master branch
```
git flow feature start [featureName]
```

- Make your changes in the feature branch only! **master branch should be kept clean**

- When finished (should be in feature branch). Note: we do not use `git flow feature finish`
```
git add -A :/[folder|files]
```
```
git commit -m "[message]"
```
Merge in changes from upstream master
```
git checkout master
```
```
git pull --rebase upstream master
```
```
git checkout feature/[featureName]
```
```
git merge master
```
Push to origin
```
git push origin feature/[featureName]
```

- Create a **Pull Request** by logging to `https://github.com/[username]/BATO/pulls`

  - At this point, you should be notified if it will merge in without conflict
  - You also should ***code review*** your changes before submitting a pull request
  - Your lead should be notified about your request after you submit


- **LEADS**: After a pull request is made, it is your reponsibility to review and merge in the changes
  - If the pull request list is showing more than 1, it is best to start on the bottom and work your way up
  - If there is any merge conflicts, the lead should notify the developer via github to resolve the issue.


#### Pulling latest from upstream and merging changes
Many merge issues can be resolved with these simple steps
```
git checkout master
```
```
git pull --rebase upstream master
```
```
git checkout feature/[featureName]
```
```
git merge master
```

#### Creating a release
Get latest from upstream
```
git checkout develop
```
```
git pull --rebase upstream master
```

Create new branch
```
git checkout -b release/[version] master
```

Merge into master and create tag
```
git checkout master
```
```
git merge --no-ff release/[version]
```
```
git tag -a [tag version]
```

Push master and tag to upstream
```
git push upstream master --no-verify
```
```
git push upstream [tag version] --no-verify
```

Merge master into develop
```
git checkout develop
```
```
git merge --no-ff master --no-verify
```

Push latest develop to upstream and origin
```
git push origin develop --no-verify
```
```
git push origin [tag version] --no-verify
```
```
git push upstream develop --no-verify
```

##### Creating a hotfix
Hotfix is the process of making a change directly into master and develop. Start with a clean develop and master.

Checkout master
```
git checkout master
```

Get latest from upstream master
```
git pull --rebase upstream master
```

Create new hotfix branch
- Note you can only have one hotfix branch at a time.

```
git checkout -b hotfix/[hotfixName] master
```

When changes are finished
```
git add [changedFiles]
```
```
git commit -m "[message]"
```

Checkout master
```
git checkout master
```

Merge hotfix into master
```
git merge hotfix/[hotfixName]
```

Push master to origin
```
git push origin master
```

Checkout develop
```
git checkout develop
```
```
git pull --rebase upstream develop
```

Merge hotfix into develop
```
git merge hotfix/[hotfixName]
```

Push develop to origin
```
git push origin develop
```

- Create a **Pull Requests** for master and develop by logging to `https://github.com/[username]/BATO/pulls`

  - At this point, you should be notified if it will merge in without conflict
  - You also should ***code review*** your changes before submitting a pull request
  - Your lead should be notified about your request after you submit

Delete the hotfix branch
```
git branch -D hotfix/[hotfixName]
```
---
