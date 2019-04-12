Tutorial 1
==============================
* This is git practice for tutorial-1.

Make repo
==============================
* Make new repo.

.. code::

    $ git init

* Add config.

.. code::

    $ git config --local user.name "cafenomad"
    $ git config --local user.email "cafenomad@outlook.com"

* Init with git-flow.

.. code::

    $ git flow init

* Show branch.

.. code::

    $ git branch 
    * develop
      master

* Show log.

.. code::

    $ git log
    commit f6fee309ea209d930c02bd2e00ee998f376135f9 (HEAD -> develop, master)
    Author: cafenomad <cafenomad@outlook.com>
    Date:   Fri Apr 12 12:05:31 2019 +0900
    
        Initial commit

* Add script.

.. code::

    mkdir src && echo 'echo "aaaaa' > src/test.sh

* Git add.

.. code::

    $ git add src/test.sh

* Git commit.

.. code::

    $ git commit -am 'Add src/test.sh'

* Show log.

.. code::
 
    $ git log
    commit 469c2f240e74e3a170c34ae837771d60937bffcb
    Author: cafenomad <cafenomad@outlook.com>
    Date:   Fri Apr 12 12:12:13 2019 +0900
    
        Add src/test.sh
    
    commit f6fee309ea209d930c02bd2e00ee998f376135f9
    Author: cafenomad <cafenomad@outlook.com>
    Date:   Fri Apr 12 12:05:31 2019 +0900
    
        Initial commit

* Relase.

.. code::

    $ git flow release start v0.0.1
    $ echo "v0.0.1" > version.txt
    $ git add version.txt
    $ git commit -am 'Add version.txt'
    $ git flow release finish v0.0.1

* Show "master" branch git log graph.

.. code:: bash

    $ git log --graph
    *   commit b520cda796164acd340a99e45365c58467bf8656 (HEAD -> master, tag: v0.0.1)
    |\  Merge: f6fee30 3b89faa
    | | Author: cafenomad <cafenomad@outlook.com>
    | | Date:   Fri Apr 12 12:27:26 2019 +0900
    | | 
    | |     Merge branch 'release/v0.0.1'
    | | 
    | * commit 3b89faa12b7032f2a3231fb5293cb5585b5fbf1b
    | | Author: cafenomad <cafenomad@outlook.com>
    | | Date:   Fri Apr 12 12:27:19 2019 +0900
    | | 
    | |     Add version.txt
    | | 
    | * commit cd2bd1fad92666f1219e071a952276f3efe85658 (origin/develop)
    | | Author: cafenomad <cafenomad@outlook.com>
    | | Date:   Fri Apr 12 12:22:44 2019 +0900
    | | 
    | |     Add README.rst
    | | 
    | * commit 469c2f240e74e3a170c34ae837771d60937bffcb
    |/  Author: cafenomad <cafenomad@outlook.com>
    |   Date:   Fri Apr 12 12:12:13 2019 +0900
    |   
    |       Add src/test.sh
    | 
    * commit f6fee309ea209d930c02bd2e00ee998f376135f9
      Author: cafenomad <cafenomad@outlook.com>
      Date:   Fri Apr 12 12:05:31 2019 +0900
      
          Initial commit

* Show "develop" branch git log graph.

.. code:: bash

    $ git log --graph
    *   commit 6f78ee9daeb0ea788819717ff5890fb975ce5f65 (HEAD -> develop)
    |\  Merge: cd2bd1f 3b89faa
    | | Author: cafenomad <cafenomad@outlook.com>
    | | Date:   Fri Apr 12 12:27:35 2019 +0900
    | | 
    | |     Merge branch 'release/v0.0.1' into develop
    | | 
    | * commit 3b89faa12b7032f2a3231fb5293cb5585b5fbf1b
    |/  Author: cafenomad <cafenomad@outlook.com>
    |   Date:   Fri Apr 12 12:27:19 2019 +0900
    |   
    |       Add version.txt
    | 
    * commit cd2bd1fad92666f1219e071a952276f3efe85658 (origin/develop)
    | Author: cafenomad <cafenomad@outlook.com>
    | Date:   Fri Apr 12 12:22:44 2019 +0900
    | 
    |     Add README.rst
    | 
    * commit 469c2f240e74e3a170c34ae837771d60937bffcb
    | Author: cafenomad <cafenomad@outlook.com>
    | Date:   Fri Apr 12 12:12:13 2019 +0900
    | 
    |     Add src/test.sh
    | 
    * commit f6fee309ea209d930c02bd2e00ee998f376135f9
      Author: cafenomad <cafenomad@outlook.com>
      Date:   Fri Apr 12 12:05:31 2019 +0900
      
          Initial commit
