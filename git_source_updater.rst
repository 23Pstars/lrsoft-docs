==================
GIT Source Updater
==================

GIT Source Updater merupakan script yang dapat membantu dalam melakukan update sebuah repo dalam deployment secara otomatis.
Update dilakukan dengan membaca setiap commit yang di-push, selanjutnya melakukan fetch raw source dari GIT server.
GIT server yang didukung saat ini hanya `BitBucket`_ dan `Github`_.

`GitHub Project`_

How to use
==========

Setup
=====

.. code-block:: php

    set_time_limit( 0 );                    // set jadi unlimited

    require_once( 'cURL.php' );             // class pembantu untuk keperluan URL
    require_once( 'GitHub.php' );           // untuk github
    require_once( 'Bitbucket.php' );        // untuk bitbucket

Tentukan credentials:

.. code-block:: php

    /** Bitbucket credentials */
    $username       = 'User';
    $password       = 'password';
    $account_slug   = 'user';
    $repo_slug      = 'repo';

.. _BitBucket: https://bitbucket.org
.. _Github: https://github.com
.. _GitHub Project: https://github.com/23Pstars/Git-Source-Updater