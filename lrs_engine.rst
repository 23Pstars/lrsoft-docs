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

Defines
-------
LRS Engine memerlukan beberapa variabel untuk menjaga konsistensi nilai maupun path.

define.abs.path.php
...................
Berisi variabel path yang dapat diakses untuk keperluan akses file sistem.

.. code-block:: php
    :linenos:

    /** absolute path untuk asset */
    define( 'LRS_ABS_ASSET_PATH', LRS_ABS_PATH . DS . 'asset' );

    /** absolute path untuk css */
    define( 'LRS_ABS_CSS_PATH', LRS_ABS_PATH . DS . 'asset' . DS . 'css' );

    /** absolute path untuk js */
    define( 'LRS_ABS_JS_PATH', LRS_ABS_PATH . DS . 'asset' . DS . 'js' );

    /** absolute path untuk js */
    define( 'LRS_ABS_IMG_PATH', LRS_ABS_PATH . DS . 'asset' . DS . 'img' );

    /** absolute path untuk content upload */
    define( 'LRS_ABS_UPLOAD_PATH', LRS_ABS_PATH . DS . 'asset' . DS . 'upload');

    /** absolute path untuk model */
    define( 'LRS_ABS_MODEL_PATH', LRS_ABS_PATH . DS . 'model' );

    /** absolute path untuk view */
    define( 'LRS_ABS_VIEW_PATH', LRS_ABS_PATH . DS . 'view' );

    /** absolute path untuk controller */
    define( 'LRS_ABS_CONTROLLER_PATH', LRS_ABS_PATH . DS . 'controller' );

    /** absolute path untuk module */
    define( 'LRS_ABS_MODULE_PATH', LRS_ABS_PATH . DS . 'module' );

    /** absolute path untuk skin */
    define( 'LRS_ABS_SKIN_PATH', LRS_ABS_PATH . DS . 'skin' );

    /** absolute path untuk version */
    define( 'LRS_ABS_VERSION_PATH', LRS_ABS_PATH . DS . 'VERSION.md' );

    /** absolute path untuk config */
    define( 'LRS_ABS_CONFIG_PATH', LRS_ABS_PATH . DS . 'config.php' );

define.uri.path.php
...................
Berisi variabel path yang dapat diakses untuk keperluan akses publik.

.. code-block:: php
    :linenos:

    /** path untuk asset */
    define( 'LRS_ASSET_PATH', LRS_URL_PATH . DS . 'asset' );

    /** path untuk css */
    define( 'LRS_CSS_PATH', LRS_URL_PATH . DS . 'asset' . DS . 'css' );

    /** path untuk js */
    define( 'LRS_JS_PATH', LRS_URL_PATH . DS . 'asset' . DS . 'js' );

    /** path untuk img */
    define( 'LRS_IMG_PATH', LRS_URL_PATH . DS . 'asset' . DS . 'img' );

    /** path untuk content upload */
    define( 'LRS_UPLOAD_PATH', LRS_URL_PATH . DS . 'asset' . DS . 'upload');

    /** path untuk module */
    define( 'LRS_MODULE_PATH', LRS_URL_PATH . DS . 'module' );

    /** path untuk skin */
    define( 'LRS_SKIN_PATH', LRS_URL_PATH . DS . 'skin' );

define.version.php
..................
Berisi variabel path yang dapat diakses untuk keperluan akses publik.

.. code-block:: php
    :linenos:

    /** versi dari LRS Engine */
    define( 'LRS_ENGINE_VERSION', $current_version );

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