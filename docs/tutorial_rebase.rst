Tutorial rebase
==============================
* This is git tutorial for rebase.

Rebase
==============================
* Commit serveral times for testing.

.. code:: bash

    $ git flow feature start tutorial_rebase

    $ git branch 
      develop
    * feature/tutorial_rebase
      master

    $ echo 'echo "bbbbb"' >> src/test.sh
    $ git commit -am 'Add "bbbbb"'

    $ echo 'echo "ccccc"' >> src/test.sh
    $ git commit -am 'Add "ccccc"'

    $ echo 'echo "ddddd"' >> src/test.sh
    $ git commit -am 'Add "ddddd"'

* show src/test.sh lines.

.. code:: bash

    echo "aaaaa"
    echo "bbbbb"
    echo "ccccc"
    echo "ddddd"

* Show git log graph.

.. code:: bash

    $ git log --graph

    * commit aa39503e2da32a4c39e3d74e53e159063291f620
    | Author: cafenomad <cafenomad@outlook.com>
    | Date:   Fri Apr 12 20:23:02 2019 +0900
    | 
    |     Add "ddddd"
    | 
    * commit 61e7b0e260a67eef59c8e1152248c478134285c0
    | Author: cafenomad <cafenomad@outlook.com>
    | Date:   Fri Apr 12 20:22:19 2019 +0900
    | 
    |     Add "ccccc"
    | 
    * commit 323d3bbb17ff91275f3ac374a10d3267d364c53c
    | Author: cafenomad <cafenomad@outlook.com>
    | Date:   Fri Apr 12 20:21:32 2019 +0900
    | 
    |     Add "bbbbb"
    | 

* Rebase!

.. code:: bash

    $ git rebase -i HEAD~3

    # [BEFORE]
    pick 323d3bb Add "bbbbb"
    pick 61e7b0e Add "ccccc"
    pick aa39503 Add "ddddd"

    # Change from "pick" to "squash".

    # [AFTER]
    pick 323d3bb Add "bbbbb"
    squash 61e7b0e Add "ccccc"
    squash aa39503 Add "ddddd"

* Show git log graph.

.. code:: bash

    $ git log --graph

    * commit df4af37a28c92973bce2efc3dec67430cef91057 (HEAD -> feature/tutorial_rebase)
    | Author: cafenomad <cafenomad@outlook.com>
    | Date:   Fri Apr 12 20:21:32 2019 +0900
    | 
    |     Add "bbbbb"
    |     
    |     Add "ccccc"
    |     
    |     Add "ddddd"

