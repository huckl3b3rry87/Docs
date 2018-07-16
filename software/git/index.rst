git
*****

Website links
==================
* https://github.com/
* The Pro Git book is available `here <https://git-scm.com/book>`_!

Useful Commands
===================
add everything to the commit (including new file and files that were deleted):
::

  git add -A

commit all of the changes:
::

  git commit -m "some message about what you did"

push to remote account:
::

  git push origin master

view current tags:
::

  git tag

making a new tag:
::

  git tag -a V0.0.1 -m " new version 0.0.1"

committing a tag:
::

  git push origin master --tags

checkout a tag:
::

  git checkout -b [branchname] [tagname]

see which branch you are on:
::

  git branch

to make a new branch:
::

   git checkout -b [name_of_your_new_branch]

to change the working branch:
::

  git checkout [name_of_your_new_branch]

to push the branch to github:
::

  git push origin [name_of_your_new_branch]

delete a local branch:
::

  git branch -d the_local_branch

delete a remote branch:
::

  git push origin --delete the_remote_branch


remove a large file from a commit that has not been pushed to master yet:
::

  git filter-branch --tree-filter 'rm -rf path/to/your/file' HEAD

connecting to github:
::

   git remote add origin git@github.com:username/new_repo

* making a branch `look here <https://help.github.com/articles/fork-a-repo/>`_

Then make a `new repository <https://github.com/new>`_ using the interweb

* Check out `this link  <http://kbroman.org/github_tutorial/pages/init.html>`_ for more info.

Caching your github password:
::

  git config --global credential.helper 'cache --timeout=3600'
  # Set the cache to timeout after 1 hour (setting is in seconds)

`Working with Remote Repositories  <https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes>`_
--------------------------------------------------------------------------------------------------------

To clone a repo:
::

  git clone https://github.com/CPFL/Autoware


To view the remote:
::

  febbo@febbo-HP-ZBook-17-G2:~/Documents/workspace/Autoware$ git remote -v
  origin	https://github.com/huckl3b3rry87/Autoware (fetch)
  origin	https://github.com/huckl3b3rry87/Autoware (push)
  upstream	https://github.com/CPFL/Autoware.git (fetch)
  upstream	https://github.com/CPFL/Autoware.git (push)

Removing a remote origin:
::

  git remote rm origin


Setting an origin:
::

  git remote set-url origin "https://..."

* Source `is this <http://stackoverflow.com/questions/13572191/cannot-remove-remote-origin>`_

Revert to an old commit:
::

  git push -f origin $old_commit_id:master

Make sure that you commit changes before moving from one branch to `another <http://stackoverflow.com/questions/32116776/git-change-on-local-branch-affects-other-local-branches>`_ the changes that you make do not belong to any particular branch!


remove files that where previously cached that are now in ``.gitignore``:
::

  git rm -r --cached .
  git add .
  git commit -am "Removed ignored files"

Update your `fork from the from the upstrean remo <https://github.com/Kunena/Kunena-Forum/wiki/Create-a-new-branch-with-git-and-manage-branches>`_:
::

  git fetch [name _of_remote]
  git fetch https://github.com/CPFL/Autoware

More info `here <https://help.github.com/articles/syncing-a-fork/>`_

To automatically `fetch and merge from a remote <https://git-scm.com/book/id/v2/Git-Basics-Working-with-Remotes>`_:
::

  git pull upstream master


Remove submodule:
::

  git rm --cached the_submodule_path

<<<<<<< HEAD
`Merging development branch with master <https://stackoverflow.com/questions/14168677/merge-development-branch-with-master>`_
------------------------------------------------------------------------------------------------------------------------------------
Merge ``master`` into ``develpment`` to see if there are any conflicts, so ``master`` remains clean:
::

  (on branch development)$ git merge master
  (resolve any merge conflicts if there are any)
  git checkout master
  git merge development (there won't be any conflicts now)

<https://stackoverflow.com/questions/27828404/why-does-git-status-show-branch-is-up-to-date-when-changes-exist-upstream>`_
`Resolving mere conflicts <https://help.github.com/articles/resolving-a-merge-conflict-using-the-command-line/>`_
----------------------------------------------------------------------------------------------------------------------
=======
Basics of Collaborating on git
===========================================
This is a beginners guide to collaborating on git. Several examples will be provided assuming ``TulgaErsal`` is collaborating with ``huckl3b3rry87`` on the ``PhD`` repo.


Getting started
----------------
This tutorial assumes that you are using a command line interface to git, for Windows consider using `cmder <http://cmder.net/>`_ and make sure that you download the full version that has git for Windows. Additionally, `Atom <https://atom.io/>`_ is a useful tool for resolving merge issues visually.

`Fork a Repository <https://help.github.com/articles/fork-a-repo/>`_
----------------------------------------------------------------------

1) Go to `github.com <https://github.com/>`_ and login. If it is a private repo that you will be collaborating on, then accept any invitations to collaborate.

2) Navigate to the repo that you will be collaberating on i.e.:
::

  https://github.com/huckl3b3rry87/PhD

3) In the top right conner of the page click ``Fork``

4) open terminal and navigate to a folder where you will be working i.e.
::

  cd Documents\workspace\

5) in the terminal, clone the forked repo that you will be collaborating on:
::

  git clone https://github.com/TulgaErsal/PhD

6) To see the current remote repo, type:
::

  git remote -v

This should say:
::

  origin  https://github.com/TulgaErsal/PhD.git (fetch)
  origin  https://github.com/TulgaErsal/PhD.git (push)

7) To add the original repo as the upstream type:
::

  git remote add upstream https://github.com/huckl3b3rry87/PhD.git

8) make sure that the upstream was added:
::

  git remote -v

Which should say:
::

  origin    https://github.com/TulgaErsal/PhD.git (fetch)
  origin    https://github.com/TulgaErsal/PhD.git (push)
  upstream  https://github.com/huckl3b3rry87/PhD.git (fetch)
  upstream  https://github.com/huckl3b3rry87/PhD.git (push)

Example 1
-------------
To make sure that you are using the most recent version of the upstream (or original repo) you need to get the latest code and merge it into your repo. Use the terminal to navigate to the git folder with the repo that you are working on. Then type:
::

  git merge upstream/master

.. note:: The above command attempts to automatically merge, and if there are merge issues they can easily be resolved using the Atom text editor.

.. note:: If you run this example just after setting everything up there should be no differences in the upstream repo.

Example 2
------------
Each day that you make changes you can push them to your local repository.

Option 1 (using Atom)
^^^^^^^^^^^^^^^^^^^^^^^
If you are using the Atom text editor, this is very easy to do.

1)  open the ``Packages`` tab and scroll down to ``Github`` and click ``Toggle Git Tab``.

2) Click ``Stage All`` to stage the changes

3) Write a commit message and click ``Commit``

4) Under the ``Commit`` button push the ``up`` arrow then click ``Push``

5) Put in your git user info

Option 2 (using terminal)
^^^^^^^^^^^^^^^^^^^^^^^^^^
1) add changes:
::

  git add -A

2) commit changes
::

  git commit -m "updated docs"

3) push changes
::

  git push origin master


Example 3
----------
This example is for when you are ready to commit to the upstream repo, this example shows you how to make a ``pull request``.

.. note: Good practice is to stay synced with the upstream repo. So, run Example 1 before this example to make sure that there are no merge conflicts that need to be resolved.

Assuming that, your local changes have all been committed to the local repo you can easily make a pull request at::
::

  https://github.com/TulgaErsal/PhD.git

Just click the ``New Pull Request`` button.

This will then alert the original repo owner and they can then merge your changes.

>>>>>>> 583ccf8843b87e3b5ba41467af531075812f8d41

Create a disconnected git branch
===================================

1) start with a fresh copy of the repo

2) Create a new disconnected branch:
::

  git checkout --orphan gh-pages

3) hop onto that branch:
::

  git checkout -b gh-pages

4) At this point there are no commits but lots of files from whatever branch you were on. Have git remove those files:
::

  git rm -rf .

then follow the rest here:

https://coderwall.com/p/0n3soa/create-a-disconnected-git-branch

::

  julia> Pkg.clone("https://github.com/JuliaMPC/MPCDocs.jl")
  INFO: Cloning MPCDocs from https://github.com/JuliaMPC/MPCDocs.jl
  INFO: Computing changes...
  INFO: No packages to install, update or remove

  julia>
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ git checkout --orphan gh-pagesSwitched to a new branch 'gh-pages'
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ branch
  The program 'branch' is currently not installed. You can install it by typing:
  sudo apt install rheolef
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ git branch
    master
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ git checkout gh-pages
  error: pathspec 'gh-pages' did not match any file(s) known to git.
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ git checkout -b gh-pages
  Switched to a new branch 'gh-pages'
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ git rm -rf .
  fatal: pathspec '.' did not match any files
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ ls
  MPCDocs  MPCDocs.jl
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ cd MPCDocs
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/.trash/MPCDocs/MPCDocs$ ls
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/.trash/MPCDocs/MPCDocs$ cd ..
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/.trash/MPCDocs$ cd MPCDocs.jl/
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/.trash/MPCDocs/MPCDocs.jl$ ls
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/.trash/MPCDocs/MPCDocs.jl$ cd ..
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/.trash/MPCDocs$ git branch
    master
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/.trash/MPCDocs$ cd ..
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/.trash$ cd ..
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5$ cd MPCDocs/
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ git branch
  * master
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ ls
  appveyor.yml  LICENSE.md  README.md  REQUIRE  src  test
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ git checkout -b gh-pages
  Switched to a new branch 'gh-pages'
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ git branch
  * gh-pages
    master
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ ls
  appveyor.yml  LICENSE.md  README.md  REQUIRE  src  test
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ git diff
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ git branch
  * gh-pages
    master
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ git rm -rf .
  rm '.codecov.yml'
  rm '.gitignore'
  rm '.travis.yml'
  rm 'LICENSE.md'
  rm 'README.md'
  rm 'REQUIRE'
  rm 'appveyor.yml'
  rm 'src/MPCDocs.jl'
  rm 'test/runtests.jl'
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ git branch
  * gh-pages
    master
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ ls
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ git clean -fdx
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ git branch
  * gh-pages
    master
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ git push origin master
  Everything up-to-date
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ git push origin gh-pages
  Total 0 (delta 0), reused 0 (delta 0)
  To git@github.com:JuliaMPC/MPCDocs.jl.git
   * [new branch]      gh-pages -> gh-pages
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$ git branch
  * gh-pages
    master
  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/MPCDocs$

Forking a Repository
=========================
`Follow what this page talks about <https://help.github.com/articles/fork-a-repo/>`_

also if you are doing this in julia `see <http://docs.julialang.org/en/release-0.4/manual/packages/>`_
Another way to connect to github it using ssh

do a:
::

  git branch


Initially the error was:
::

  febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/VehicleModels$ git push origin master
  Permission denied (publickey).
  fatal: Could not read from remote repository.

  Please make sure you have the correct access rights
  and the repository exists.

* This was obtained when initially setting up the git repositories in julia after cloning a package and trying to push modifications back up to the remote repository.
* Information on this can be founds `at <http://docs.julialang.org/en/release-0.5/manual/packages/>`_ , or by following the two steps a fix may be obtained:

FOLLOW:

https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/

NOTE: just hit enter, don't change the default location!!!
THEN:

https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/


  1. Make an ssh key and add it to github, `following  <https://github.com/settings/ssh>`_.

  2. Check out `this <https://linux.die.net/man/1/ssh-agent>`_, or use the following commands:

    * A program to hold private keys for public authentication.

      type:
      ::

        ssh-agent

    * Initially the agent does not hold any private keys.

      So run:
      ::

        ssh-add


Mistakes I Made
====================

* Make sure that you are working on the master branch!

    * Do not check out a tag and start making changes only to realize that you are not on the master branch!


* Trying to connect to github using ssh

  1) Create a github repository, with the name ( for example: huckl3b3rry87/LiDAR.jl )


  2) Then

  Type this in the terminal:
  ::

    febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/LiDAR$ git remote add origin git@github.com:huckl3b3rry87/LiDAR.jl

  3) Then

  Try this:
  ::

    febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/LiDAR$ git pull master

  4) Next

  Get this:
  ::

    fatal: 'master' does not appear to be a git repository
    fatal: Could not read from remote repository.

    Please make sure you have the correct access rights
    and the repository exists.

  Next we are going to `test the ssh connection <https://help.github.com/articles/testing-your-ssh-connection/>`_

  5) Attempt to ssh to GitHub
  By typing:
  ::

    febbo@febbo-HP-ZBook-17-G2:~/.julia/v0.5/LiDAR$ ssh -T git@github.com
    Hi huckl3b3rry87! You've successfully authenticated, but GitHub does not provide shell access.

  6) realize that you messed up
  by typing:
  ::

    git pull master

  and not:
  ::

    git pull origin master
