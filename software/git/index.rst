git
=====

Website links
--------------

* https://github.com/
* The Pro Git book is available `here <https://git-scm.com/book>`_!

Useful Commands
-----------------

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

Update your `branch from the original branch <https://github.com/Kunena/Kunena-Forum/wiki/Create-a-new-branch-with-git-and-manage-branches>`_:
::

  git fetch [name _of_remote]
  git fetch https://github.com/CPFL/Autoware

To automatically `fetch and merge from a remote <https://git-scm.com/book/id/v2/Git-Basics-Working-with-Remotes>`_:
::

  git pull upstream master


Remove submodule:
::

  git rm --cached the_submodule_path

Create a disconnected git branch
------------------------------------

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
---------------------
`Follow what this page talks about <https://help.github.com/articles/fork-a-repo/>`_

also if you are doing this in julia `see <http://docs.julialang.org/en/release-0.4/manual/packages/>`_
Another way to connect to github it using ssh

do a:
::

  git branch

----------------------------------------------
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
----------------
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
