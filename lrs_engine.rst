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
Buat script ``config.php`` pada `root` yang berisi konfigurasi utama untuk menentukan beberapa variable yang digunakan dalam Engine.

.. code-block:: php
    :linenos:

    /** ========================
     * konfigurasi path dan url
     * ====================== */

    /** app url path */
    define( 'LRS_URL_PATH', 'http://localhost/lrsoft/lrs-engine' );


    /** =======================
     * Informasi umum aplikasi
     * ===================== */

    /** app name */
    define( 'LRS_APP_NAME', 'Local Development' );

    /** app author */
    define( 'LRS_APP_AUTHOR', 'LRsoft Corp.');

    /** app author url */
    define( 'LRS_APP_AUTHOR_URL', 'http://lrsoft.co.id');


    /** =====================
     * konfigurasi database
     * ==================== */

    /** host */
    define( 'LRS_DB_HOST', 'localhost' );

    /** username */
    define( 'LRS_DB_USERNAME', 'user' );

    /** password */
    define( 'LRS_DB_PASSWORD', 'pass' );

    /** database name */
    define( 'LRS_DB_NAME', 'dbname' );

    /** prefix tabel */
    define( 'LRS_DB_PREFIX', 'lrs_' );

    /** installer enable */
    define( 'LRS_INSTALLER_ENABLE', true );


    /** load fungsi inti lainnya */
    require_once( 'function.php' );


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

Functions
---------
Berisi fungsi-fungsi pendukung yang banyak digunakan dalam Core, Modules, dan Skins.

.. php:class:: fn.engine.php

  Daftar fungsi untuk keperluan engine.

  .. php:method:: check_required_engine_version( $required_version, $exit, $messages )

      Memeriksa kebutuhan versi engine untuk verifikasi module dan skin.

      :param string $required_version: Versi engine yang ingin dicek.
      :param string $exit: Jika tidak sesuai, apakah langsung exit atau tidak (default ``true``).
      :param string $messages: Pesan ketika exit (default ``Insufficient Version of Engine``).

  .. php:method:: is_admin_page()

      Cek apakah suatu halaman merupakan halaman admin atau tidak

      :returns: yes | no

  .. php:method:: sync_default_params( $default, $destination )

      Melakukan singkronisasi terhadap 2 array

      :param array $default: Array default sebagai sumber.
      :param array $destination: Array tujuan.

  .. php:method:: in_array_r( $needle, $haystack )

      Melakukan pencarian secara rekursif didalam array multidimensi

      :param string $needle: Nilai yang akan dicari.
      :param array $haystack: Array tujuan.

  .. php:method:: lrs_exit( $messages = '', $type = 'info' )

      Menampilkan format pesan error pada saat exit (menghentikan script denagn paksa)

      :param string $messages: Nilai yang akan dicari (default string kosong, tapi script tetap ``exit()``).
      :param string $type: Jenis pesan (info | alert).

  .. php:method:: lrs_redirect( $target = LRS_URL_PATH )

      Melakukan redirect (mengarahkan) ke sebuah halaman tertentu sesuai parameter

      :param string $target: Halaman tujuan.

  .. php:method:: get_menus( $array )

      Mendapatkan built in menu, dari daftar `Pages`

      - ``post_type``: jenis `post` ( post | page )
      - ``post_parent``: ID untuk page induk
      - ``post_status``: publish | draft
      - ``orderby``: order berdasarkan suatu field
      - ``order``: ASC | DESC
      - ``number``: jumlah output maksimum item

      :param array $array: Array yang berisi key.

  .. php:method:: validate_url()

      Memastikan konsistensi URL antara `requests` dan ``config.php`` dengan melakkukan redirect.

  .. php:method:: lrs_paging_nav( $base_url, $total_data, $current_page, $data_per_page = 10, $range_data = 3 )

      Membantu membuat navigasi halaman berdasarkan query database.

      :param string $base_url: URL dasar pembentukan navigasi
      :param int $total_data: Total keseluruhan data
      :param int $current_page: Halaman saat ini
      :param int $data_per_page: Jumlah data tiap page
      :param int $range_data: Range data pada list navigasi, misal: ``1`` ``...`` ``23`` ``24`` ``25`` ``26`` ``27`` ``...`` ``100``

  .. php:method:: is_SSL_URI()

      Cek apakah URI yang ada pada ``config.php`` adalah `HTTPS`

  .. php:method:: is_SSL_request()

      Cek apakah URI yang di-submit merupakan `HTTPS`

  .. php:method:: minify_HTML_output()

      Melakukan kompresi out HTML dengan menghilangkan whitespace yang tidak diperlukan. Masukkan ``ob_start( 'minify_HTML_output' )`` pada bagian awal dan ``ob_end_flush()`` pada bagian akhir script.

Models
------

.. _Model Post:

Post
....
Model `Post` berfungsi sebagai objek untuk menyimpan data-data sebuah post, diantaranya:

- ``$post_id`` ID unik dari sebuah post.
- ``$post_status`` (active | inactive)
- ``$post_type`` (Post | Page)
- ``$post_title`` Judul utama dari sebuah post.
- ``$post_name`` Judul post dalam format URL, biasanya digunakan untuk `permalink`.
- ``$post_content`` Materi dari post.
- ``$post_thumbnail_image`` Image thumb, biasanya berukuran kecil.
- ``$post_featured_image`` Image cover, biasanya berukuran cukup besar.

Model `Post` berada pada ``/model/Post.php``, dan berisi beberapa method pendukung berikut:

.. php:class:: Post.php

  Daftar method objek post untuk menyimpan data.

  .. php:method:: init( $post )

      Init `value` sekaligus dalam waktu bersamaan.

      :returns: Object `post`.

  .. php:method:: get_{property_name}()

      Mendapatkan nilai dari masing-masing `property name`.

      :returns: `property value`

  .. php:method:: set_{property_name}( $value )

      Memberikan nilai ke masing-masing `property name`.

      :param int|string $value: Nilai untuk masing-masing `property`.

  .. php:method:: set_{property_name}( $value )

      Memberikan nilai ke masing-masing `property name`.

      :param int|string $value: Nilai untuk masing-masing `property`.

  .. php:method:: get_permalink( $structured = false )

      Mendapatkan `URL` ke masing-masing post, format ``$structured`` adalah ``/category/post-name``, dan default ``/post-name``.

      :returns: String dalam format `URL`.

  .. php:method:: is_empty( $field = 'post_id' )

      Memeriksa apakah objek `Post` NULL (kosong), beberapa field yang bisa dicek:

      - ``post_name``
      - ``post_title``
      - ``post_content``
      - ``post_date``

      :returns: Boolean (true|false).


Controllers
-----------
Kelas-kelas yang berisi fungsi inti dari setiap bagian layanan.

Posts
.....
Controller `Posts` berfungsi untuk mendapatkan data `post` dari database, kelas ini berada dalam direktori ``/controller/`` dan terdiri dari beberapa method.

.. php:class:: Posts.php

  Daftar method untuk keperluan management post dari database.

  .. php:method:: get_instance()

      Method static yang dapat dipanggil tanpa melakukan instansiasi, berguna untuk memanggil secara cepat kontroller ``Posts``, caranya ``Posts::get_instance()->{method}``.

      :returns: Objek kontroller ``Posts``.

  .. php:method:: get_post( $post_id, $by = 'post_id', $meta_key = '', $meta_value = '' )

      Mendapatkan 1 objek post dari database dengan mapping dari `Model Post`_.

      :returns: Objek `Model Post`_.

  .. php:method:: get_posts( $params = array() )

      Mendapatkan beberapa objek post `Model Post`_ sekaligus dengan beberapa parameter berikut:

      - ``post_title`` judul dari post, `default` `empty`
      - ``post_content`` isi dari post, `default` `empty`
      - ``post_type`` jenis post, `default` `Post` (`Post` | `Page` | -1)
      - ``post_parent`` ID dari post induk, `default` -1
      - ``post_status`` status post, `default` `Publish` (`Publish` | `Draft` | -1)
      - ``exclude`` array dari ID `Model Post`_ yang tidak ingin dimunculkan dalam hasil, `default` ``array()``
      - ``category_id`` ID dari kategory, `default` -1
      - ``category_exclude`` ID dari kategori yang tidak ingin dimunculkan dalam hasil, `default` ``array()``
      - ``post_month`` bulan pembuatan post, `default` -1
      - -tbd-

      :returns: Array dari objek `Model Post`_.


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