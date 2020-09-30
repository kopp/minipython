Module Development
------------------

This tutorial will help you get started building your own custom modules for MiniPython.

You will learn how to add the hello module example into MiniPython step-by-step.

STEP 1: Clone 
+++++++++++++
MiniPython Repo
.. code-block:: console
    git clone https://github.com/mytechnotalent/minipython.git

STEP 2: Copy
++++++++++++
Copy LATEST make-frozen.py Module
`make-frozen.py <https://github.com/micropython/micropython/blob/master/tools/make-frozen.py>`_

STEP 3: Create
++++++++++++++
Create and edit hello.py as follows::

    print('hello')

PLACE FILE IN THE frozen/firmware DIRECTORY AS hello.py

STEP 4: Transform
+++++++++++++++++
Transform hello.py To hello.c
.. code-block:: console
    python tools/make-frozen.py <GIT_REPO_FOLDER_PATH>/frozen/firmware > hello.c

STEP 5: Move
++++++++++++
Move hello.c
MOVE FILE TO THE source/py DIRECTORY AS hello.py

STEP 6: Edit
++++++++++++
Edit inc/genhdr/mpversion.h
CHANGE LINE 2::
    #define MICROPY_GIT_TAG "Hello MOD v1.0.0 <VERSION_PROVIDED_IN_FILE>"
CHANGE LINE 4::
    #define MICROPY_BUILD_DATE "<DATE>"

STEP 7: Flash
+++++++++++++
Flash Firmware
`Instructions <https://github.com/mytechnotalent/minipython>`_