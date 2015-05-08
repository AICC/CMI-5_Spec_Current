CMI-5 Current Working Draft
---

*If you have questions, suggestions, or concerns about this specification, please post an issue to [this GitHub repository](https://github.com/AICC/CMI-5_Spec_Current).*<br>
*By using this repository, you are agreeing to the terms of the license agreement defined in license.txt.*<br>
*Note that this is a working draft and is NOT intended for implementation.*<br>


# Workflow for Editing the CMI-5 Specification
----

## Set Up
If you are not currently working with GitHub and git, follow these set up steps
first. GitHub provides excellent help at <https://help.github.com/articles/set-up-git>.

### Sign Up for a GitHub Account
If you do not already have a GitHub account, [sign up](https://github.com/signup/free).


### Fork the CMI-5 Repository
Go to the CMI-5 repository. Fork the repository to your own account using
the "Fork" button on the top right of CMI-5 repository page. This makes a
copy of the CMI-5 repository. This fork gives you the ability to edit your
version of the document without impacting the master copy.


### Install Git (use the cmd line) or Install Windows/Mac GitHub Client
You need to install Git to work with a GitHub repository. If you are on a PC (Windows),
you can download the GitHub client app. If you use a Mac, you can download the GitHub
client app, but you will also have to download git to add a remote to the master repository.
Otherwise, install git from the git site.

__Git__

This provides a command line client app for working with a git repository (like GitHub)
Download and run [git install](http://git-scm.com/downloads).

__GitHub Client__

GitHub Client provides a GUI interface to simplify working with a repository on GitHub.
This does not currently support synchronizing with a master repository, so some commands
will still need to be completed using the command line.

+ __Mac:__ <http://mac.github.com/>
+ __Windows:__ <http://windows.github.com/>


### Clone Your GitHub Fork to Your Machine
To make edits and work on the files in the repository, clone your repository to your local
machine using Git. The url is provided on the home page of your repository
(ex. ```https://github.com/<your username>/CMI-5_Spec_Current/```)

__Git__
```git
git clone https://github.com/<your username>/CMI-5_Spec_Current/
```

__GitHub Client__

On the home screen of the client app, select your account under "GitHub" and choose the
repository you want to clone. Selecting the repository from the list gives you an option
to clone it.

### Add CMI-5 repository as upstream remote
Add a remote repository to git to reference the master repository. This will make
synchronizing with the master repository a bit easier.

__Git__

```git
git remote add upstream https://github.com/AICC/CMI-5_Spec_Current
```

__GitHub Client__

Currently, the GitHub clients don't have a way to synchronize with the master repository.
In order to do this, open your repository on the GitHub client app home screen. On the
repository screen, select <b>Tools > Open a Shell Here</b>. Alternatively, use the
"Git Shell" shortcut if it was created during installation. **NOTE:** If you're using a
Mac, there is no shell shortcut so navigate to:
```shell
/your/repo/path/CMI-5_Spec_Current
```
then follow the shell instructions.

In the shell, enter:
```git
git remote add upstream https://github.com/AICC/CMI-5_Spec_Current
```


## Workflow

### Sync Up with the Master CMI-5 Repository
Pull down changes from the master repository. This automatically does a fetch of the
master repository and a merge into your local repository.

__Git and GitHub Client__
```git
git pull upstream master
```

### Make Changes Locally
Edit the local copy of the file, save and commit. Rule of thumb: Use commits like save
points. Commit to indicate logical groups of edits, and places where the edits could be
safely rolled back.

__Git__
```git
git commit -a -m '<commit message>'
```

__GitHub Client__

The GitHub client will detect saved changes to the documents in your local repository and
present a button to commit your edits at the top right of the repository screen.

### Push Changes to Your Repository (Origin)
Pushing your changes to your remote GitHub repository stages the files so that you can
then make requests to the master repository to merge in your changes.

__Git__
```git
git push origin
```

__GitHub Client__

The GitHub client has a "sync" button at the top of the repository screen. This will
synchronize your local and remote (origin) repository.

### Submit a Pull Request to the Master CMI-5 Repository (Upstream)
When you forked from the CMI-5 repository, a link back to the master repository was
created. To send your changes back to the the master repository, click the "Pull Request"
button at the top of your repository page. This will direct you to a page that gives you
the ability to submit a request to the master repository to merge in the changes you
committed.
