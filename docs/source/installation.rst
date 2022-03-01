Usage
=====
.. _requirements:

Requirements
------------
- [XAMPP with PHP 8.0 or higher](https://www.apachefriends.org/index.html)
- PHP installed in PATH variables (done by XAMPP or composer automatically)
- [Composer](https://getcomposer.org/)
- Access to the restricted github page (Ask RedFirebreak or any collaborator for access)

After installing all the programs, make sure to PHP

.. _installation:

Installation
------------
.. note::
   This is only required if you want to `develop` for the project, want to see or use the project? Go to the [dev website](https://dev.genericwebsitename.nl/) or the [main website](https://www.genericwebsitename.nl/).

Start your XAMPP apache and heidisql. After that, to test and develop this project locally, first clone it from the main repository,:

.. code-block:: console
   (cmd) $ cd {path/to/xamp/htdocs}
   (cmd) $ git clone https://github.com/RedFirebreak/OpenICT-Checkin.git

Now, preferring on your installation choice, move the insides of the now downloaded folder to your preferred web-space. You do not have to keep the path specified in this tutorial, as long as you know where you store the pulled github files

In the project folder, copy the ``.env.example`` to a new file called ``.env`` and fill in the config file. By default, you can use `root` as the database password with an empty password.

.. note::
   Make sure to prepare the required database in advance. If no database is present, the application will **NOT** load and you will see a `500: error`

After cloning, go into path of the cloned folder and keep the terminal open
.. code-block:: console
   (cmd) $ cd {path/to/xamp/htdocs/project}
   (project/) $ 

And switch to the dev branch for your developing
.. code-block:: console
   (project/) $ git checkout dev

With the still opened terminal, peform the following commands:
.. code-block:: console
   (project/) $ composer install
   (project/) $ composer update
   (project/) $ composer dump-autoload
   
   (project/) $ php artisan key:generate

This will install all the required filed, make sure they are updated and set them up for auto-loading. After this, you will generate your own security key for the application.

Technically, you should now see the project as below! 
![Homepage](https://github.com/RedFirebreak/OpenICT-Checkin-Docs/tree/main/docs/images/frontpage.png)

.. note::
   Make sure to prepare the required database in advance. If no database is present, the application will **NOT** load and you will see a `500: error` page instead of the image above.

.. _updating:
Updating
------------
To update the application, move a cmd to the project directory and peform the following commands:
.. code-block:: console
   (cmd) $ cd {path/to/xamp/htdocs/project}
   (project/) $ 

.. code-block:: console
   (project/) $ git pull
   (project/) $ composer update

The application is now up to date with the dev branch as you should see on the [development website](https://dev.genericwebsitename.nl/)


Usage
----------------

INCOMPLETE

Contents
--------

.. toctree::
	requirements
   installation
   updating
   usage