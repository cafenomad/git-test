Tutorial rebase edit
==============================
* This is git tutorial for old commit edit.

Rebase for old commit edit
==============================
* Specify the hash id(One before) from commit log.

.. code:: bash

    # Rebase for edit.
    $ git rebase -i 04cc8bdfa7326f821a186efd16d6f5b7856254de

    # Change from "pick" to "edit".
    pick e5332de Add "bbbbb" 
    edit e5332de Add "bbbbb" 

* These lines displayed.

.. code:: bash

    Stopped at e5332de...  Add "bbbbb"
    You can amend the commit now, with
    
      git commit --amend 
    
    Once you are satisfied with your changes, run
    
      git rebase --continue

* Show log(Changed HEAD).

.. code:: bash

    $ git log

    commit e5332de6d4f3837a89a532955975791157ed7690 (HEAD)
    Author: cafenomad <cafenomad@outlook.com>
    Date:   Fri Apr 12 20:21:32 2019 +0900
    
        Add "bbbbb"
        
        Add "ccccc"
        
        Add "ddddd"
        
        Add docs/tutorial_rebase.rst
     
* Edit the file.

.. code:: bash

    $ vim docs/tutorial_rebase.rst
    $ git diff
    $ git add docs/tutorial_rebase.rst
    $ git commit --amend

    # Finish the rebase and back latest stage.
    $ git rebase --continue

    # If you want to reject the rebase, then should use abort option.
    $ git rebase --abort

How to push the amended commit to the remote repo.
======================================================
* You will get an error if you push it.

.. code:: bash

    $ git push origin develop
    Username for 'https://github.com': cafenomad
    Password for 'https://cafenomad@github.com': *****
    To https://github.com/cafenomad/git-test.git
     ! [rejected]        develop -> develop (non-fast-forward)
    error: failed to push some refs to 'https://github.com/cafenomad/git-test.git'
    hint: Updates were rejected because the tip of your current branch is behind
    hint: its remote counterpart. Integrate the remote changes (e.g.
    hint: 'git pull ...') before pushing again.
    hint: See the 'Note about fast-forwards' in 'git push --help' for details.

* Fetch.

.. code:: bash

    $ git fetch origin develop
    From https://github.com/cafenomad/git-test
     * branch            develop    -> FETCH_HEAD

* Check the diff.

.. code:: bash

    $ git diff --shortstat develop..origin/develop
    1 file changed, 6 insertions(+), 5 deletions(-)

* Merge.

.. code:: bash

    $ git merge origin/develop
    Auto-merging docs/tutorial_rebase.rst
    CONFLICT (add/add): Merge conflict in docs/tutorial_rebase.rst   # <- edit!
    Automatic merge failed; fix conflicts and then commit the result.

* Fix the conflict.

.. code:: bash

    vim docs/tutorial_rebase.rst

* Check diff.

.. code:: bash

    $ git diff
    diff --cc docs/tutorial_rebase.rst
    index 5d90462,d0a9318..0000000
    --- a/docs/tutorial_rebase.rst
    +++ b/docs/tutorial_rebase.rst

* Add and commit.

.. code:: bash

    $ git commit -am 'Fix the docs/tutorial_rebase.rst conflict'
    [develop 2b4adcb] Fix the docs/tutorial_rebase.rst conflict

* Push to remote.

.. code:: bash

    $ git push origin develop
    Username for 'https://github.com': cafenomad
    Password for 'https://cafenomad@github.com': ******
    Enumerating objects: 12, done.
    Counting objects: 100% (12/12), done.
    Delta compression using up to 8 threads
    Compressing objects: 100% (7/7), done.
    Writing objects: 100% (7/7), 832 bytes | 416.00 KiB/s, done.
    Total 7 (delta 4), reused 0 (delta 0)
    remote: Resolving deltas: 100% (4/4), completed with 2 local objects.
    To https://github.com/cafenomad/git-test.git
       48e7394..2b4adcb  develop -> develop

