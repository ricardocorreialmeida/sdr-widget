# INTRODUCION #

Here is an updated text for this wiki entry. Old text not deleted, see below.

Git is a version control system. It is very practial for distributed online projects like the SDR-Widget / Audio-Widget. But it IS a learning
curve which shouldn't be underestimated. So read up on tutorials to get a feeling for it. For me the one which gave me the sort of aha feeling
I needed to trust git as a tool was this one: http://ftp.newartisans.com/pub/git.from.bottom.up.pdf

The git repository is located at https://github.com/borgestrand/sdr-widget You can view branches and their files from there.


# GIT SETUP #

Perhaps the most confusing thing about using git and github (the central repository) is all the setting up you have to do to get there. Things
are fairly well documented, but be prepared to follow this list religiously and maybe redo the whole thing.

First of all, get yourself a working installation of cygwin or Linux. Packages "git", "ssh" and "make" will be required.

Github's own tutorial is focused on a GUI. Still, it is very instructive. Read it at http://help.github.com/win-set-up-git/
In a shell the setup goes something like this:

Register with a user name and password at https://github.com/ Remember your credentials as your\_github\_username and your\_github\_password

If you need write acces, request priviledges from repository owner Borge. He'll need to know your\_github\_username

You'll need to make SSH keys with

**ssh-keygen -t rsa -C "your@mail.address.com"**

Make backups of id\_rsa.pub and id\_rsa. Personally, I keep my local project files on a memory stick which tours different computers. My user account
on all those computers need those same id\_rsa files. Their default location is /home/username/.ssh That's where you want copies of your backup
files to end up if you're using other computers.

Go to www.github.com -> Login -> Account Settings (top right center icon)

> -> SSH Keys -> Add SSH Key -> Paste in id\_rsa.pub

**git config --global user.name "Your Real Name"**

**git config --global user.email "your@mail.address.com"**

**git config --global user.password "yourpassword"**

Not sure if the one above is really needed....

**git config --global github.user "your\_github\_username"**

**git config --global github.password "your\_github\_password"**

**ssh -T git@github.com**

Are you sure .... -> yes
Should produce
Hi your\_github\_username!....

That should be it....


# CLONING #

**git clone git@github.com:borgestrand/sdr-widget.git**

Will set up local copies of what is stored in the central repository. By now you should have a bit of a grasp about git's consept of branches.
If you don't, go back to the tutorials and reread them.

It is important that your work is done in your own locally stored scratchbook / sandbox etc. That gives you the ability to change and discard
things without too large consequences. To get started, first check out the centrally stored branch you wish to use as a starting point:

**git checkout audio-widget-experimental**

Then - and only then - establish your local branch. It is very important that the branch name you choose is NOT the name of a centrally stored
branch. You reach those with git checkout. "git branch" is like "ls" or "dir". "git branch xxx" is something you don't do without really
wanting to establish the branch xxx. You establish the new local branch with:

**git branch local-branch**

Start working on your local branch:

**git checkout local-branch**

You should now be set to start editing or browsing the code.



# UPDATING AND EDITING #

Get recent updates from other users.

**git pull**

Make sure you're working on your local branch with:

**git checkout local-branch**

Merge the currently checked-out (your local-branch) branch with the one specified below (audio-widget-experimental). In this
case the changes other users committed into the centralized branch audio-widget-experimental will be merged into your local-branch.

**git merge audio-widget-experimental**

At this point in time you can open up your favourite editor. Make sure you've done all the checkout'ing first. Otherwise the editor might
get confused about the files which changed on your file system.

Edit, compile, test, be marry. To compile your code you will need Atmel's AVR32 Toolchain version 2.7 from http://www.atmel.no/beta_ware/.
Building the code takes a command like "make clean audio-widget". But to understand things, have a look at files "Makefile" and "make-widget"
at the project root directory.

At some point of time you may be happy with the changes and want to share them. To do that, first make sure your local-branch is up to date.

**git commit -am "Text describing your recent edits"**

The 'a' in -am makes sure your changes are added. The 'm' part means the message follows. This is to prevent git from trying to open an editor
to record the message.

Now, close your editors because you're about to change to a branch to be used to write back to the repository. In this branch files may look
a bit different before your changes are merged into it.

**git checkout audio-widget-experimental**

This is your local copy of the repository-stored branch. To put your recent edits into this local copy, do

**git merge local-branch**

Rembember, the specified branch is merged into the current branch. The last step remaining is to update the central repository with your changes.

**git push**

If this went well, your changes are in the central repository. And other users can pull them from there. For good measure, go back to your
local-branch so that any changes you do will end up there.


# PREVIOUS VERSION OF THIS TEXT #

# Introduction #

There exists a git repository for the firmware code in this project. This page is under construction!


# Site #

The git repository is located at https://github.com/amontefusco/sdr-widget

# Getting Started #

You may install an Eclipse plugin which works with AVR32studio. With AVR32studio installed, add the git plugin from ...
Install by following these steps:

  * Download ...
  * ...

On Cygwin, search for "git" packages in setup.exe and install them. On a Linux system with apt run "apt-get install xxx". For both, with the command line you can follow these steps to get started:

  * Make a local directory for your copy of the repository, here: "github".
  * cd github
  * git clone git://github.com/amontefusco/sdr-widget.git
  * cd sdr-widget
  * git checkout master (Change branch)
  * git branch sdr-widget-local (Create local branch)
  * git checkout sdr-widget-local (Switch to local branch)
  * At this stage you can import github/sdr-widget into AVR32studio. Don't forget to change the target to Release.
  * ...
The latest from Roger:

  * clone the github repository
> > git clone git://github.com/amontefusco/sdr-widget.git
  * change directory into the clone, so git knows what you're talking about
> > cd sdr-widget
  * tell git to grab all the branches and tags
> > git fetch origin
  * checkout the master branch
> > git checkout master
  * set an environment variable to locate your avr32-gcc
> > export AVR32BIN=where-ever-it-is
  * make Release/widget.elf and ./widget-control
> > make


# Reading and Writing #

Downloading data from the git repository is called "checkout" while uploading data is called "commit". Checkouts can be done anonymously, but commits require user priviledges.

  * Register at https://github.com/
  * Request priviledges from Andrea...

See above section for your initial checkout.

To create local branch from master:

**git checkout master**


**git branch sdr-widget-local**

If u mess everything up in local, u can delete the branch completely:

**git branch -D sdr-widget-local**

You can update the latest sdr-widget-2:

**git checkout master**


**git pull**

To incorporate the latest pull into your local:

**git checkout sdr-widget-local**

**git merge master**

Conversely, to incorporate your local changes into sdr-widget-2:

**git checkout master**

**git merge sdr-widget-local**

After that, u can (with write permission) push your changes to the
github:

**git push**

If u are not sure, u can use the git email instructions to email your
changes as patch files for developers with write access to do the
merge and push for u.

# More details #

Not yet fully edited. You'll have to go through these steps before your code goes into the shared online repository.



See details at http://help.github.com/win-set-up-git/
then:
ssh-keygen -t rsa -C "your@mail.address.com"

Go to www.github.com -> Login -> Account Settings (top right)

> -> SSH Public Keys -> Add another... -> Paste in id\_rsa.pub

git config --global user.name "Borge Strand-Bergesen"

git config --global user.email "your@mail.address.com"

git config --global user.password "yourpassword"

git config --global github.user "yourusername"

git config --global github.password "yourpassword"

Not sure if this step is needed:
Go to www.github.com -> Login -> Account Settings (top right)
> -> Account Admin (left) -> API Token
git config --global github.token 123123123123123token

Now you can start accessing code if you intend to push your changes back!

git clone git@github.com:amontefusco/sdr-widget.git

Follow above instructions for local branches, merges etc.

After adding creating file.txt

git add file.txt

After doing your edits:

git commit -a -m 'Message: what did you change?'

If you're really sure your changes belong in the remote github repository:

git push



# git Documentation #

Some git documentation can be found at:
  * http://www.kernel.org/pub/software/scm/git/docs/user-manual.html
  * http://www.kernel.org/pub/software/scm/git/docs/gittutorial.html
  * http://gnuradio.org/redmine/wiki/gnuradio/DevelopingWithGit
  * http://blog.xkoder.com/2008/08/13/git-tutorial-starting-with-git-using-just-10-commands/