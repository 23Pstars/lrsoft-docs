==========
LRS Engine
==========

**LRS Engine** adalah web based CMS yang dikembangkan untuk fokus pada kinerja dan skalabilitas, dibangun dengan konsep `MVC`_ sehingga sangat mendukung agile development.

Secara umum **LRS Engine** terbagi menjadi 3 bagian yakni *Core*, *Modules*, dan *Skins*. Masing-masing bagian bertujuan untuk membatasi ruang kerja pengembangan, sehingga tidak akan mengganggu bagian program lainnya.

Core
====
Core merupakan inti dari LRS Engine, dimana memuat class untuk semua kebutuhan web. Pada dasarnya LRS Engine merupakan platform untuk bloging.
Fitur dasar seperti Posts, Pages, Media, dan lain sebagainya secara native telah tersedia.

- konfigurasi
- defines
- controller

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