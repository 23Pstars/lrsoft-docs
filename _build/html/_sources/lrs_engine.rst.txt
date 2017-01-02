==========
LRS Engine
==========

**LRS Engine** adalah web based CMS yang dikembangkan untuk fokus pada kinerja dan skalabilitas, dibangun dengan konsep `MVC`_ sehingga sangat mendukung agile development.

Secara umum **LRS Engine** terbagi menjadi 3 bagian yakni *Core*, *Modules*, dan *Skins*. Masing-masing bagian bertujuan untuk membatasi ruang kerja pengembangan, sehingga tidak akan mengganggu bagian program lainnya.

Core
====
Core merupakan inti dari LRS Engine, dimana memuat class untuk semua kebutuhan web. Pada dasarnya LRS Engine merupakan platform untuk bloging.
Fitur dasar seperti Posts, Pages, Media, dan lain sebagainya secara native telah tersedia.

Configuration
-------------
Script ``config.php`` pada ``root`` merupakan konfigurasi utama untuk menentukan beberapa variable yang digunakan dalam Engine dan modul-modul yang akan digunakan.

PHP.ini override
................

.. code-block:: php
    :linenos:

    error_reporting( E_ALL ^ E_DEPRECATED );        // untuk keperluan debugging
    date_default_timezone_set('Asia/Makassar');     // set zona waktu

URL Path
........
local path (development) atau real domain (production)

.. code-block:: php
    :linenos:

    define( 'LRS_URL_PATH', 'http://localhost/lrsoft/lrs-engine' );     // change me

Modules
.......
Tidak harus menggunakan semua module, include hanya yang dibutuhkan saja.

.. code-block:: php
    :linenos:

    $LRS_APP_MODULES = array(
        array(
            'name' => 'Mailer',
            'path' => 'mailer'
        ),
        array(
            'name' => 'DB Exporter',
            'path' => 'db-exporter'
        ),
    );

General Info
............
Informasi umum aplikas web

.. code-block:: php
    :linenos:

    define( 'LRS_APP_NAME', 'LRsoft Engine' );
    define( 'LRS_APP_AUTHOR', 'LRsoft Corp.');
    define( 'LRS_APP_AUTHOR_URL', 'http://lrsoft.co.id');

Database
........

.. code-block:: php
    :linenos:

    define( 'LRS_DB_HOST', 'localhost' );
    define( 'LRS_DB_USERNAME', 'user' );
    define( 'LRS_DB_PASSWORD', 'pass' );
    define( 'LRS_DB_NAME', 'lrs_engine_v2.1.0' );
    define( 'LRS_DB_PREFIX', 'lrs_' );

Installer
.........
Install semua struktur dan pre-installed database pada LRS Engine.

.. code-block:: php
    :linenos:

    define( 'LRS_INSTALLER_ENABLE', true );

- defines
- controller
- model

Modules
=======

- db exporter
- mailer
- nationality
- currency
- fastboat
- tour
- flight

Skins
=====
- structure

.. _MVC: https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller