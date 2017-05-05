============
API Services
============

Tim research and development LRsoft telah mengembangkan beberapa API untuk keperluan project. Beberapa API sengaja dibuka ke publik sebagai bahan inspirasi, meskipun beberapa lagi diantaranya tidak benar-benar terbuka (licensed).

Boat Price
==========

API yang dapat menampilkan history harga kapal cepat (fast boat) yang melalui Bali, Lombok, dan pulau-pulau Gili.

``http://api.lrsoft.id/boat-price/v1/``

Currency Rate
=============

API yang dapat menampilkan nilai konversi dari beberapa mata uang yang umum digunakan di banyak negara.

.. php:class:: http://api.lrsoft.id/currency-rate

  Versi 1

  .. php:method:: /v1/gets( $array )

      Menampilkan daftar nilai konversi mata uang.

      - ``sync_date`` tanggal rate, `default` tanggal saat ini
      - ``base`` dasar nilai konversi, `default` `IDR`
      - ``name`` mencari nama mata uang negara, `default` `empty`
      - ``order_by`` mengurutkan daftar nilai konversi, `default` `sync_date` (`sync_date` | `base` | `name` | `code` | `value`)
      - ``order`` mode pengurutan, `default` `DESC` (`DESC` | `ASC`)
      - ``order`` jumlah data, `default` `10`
      - ``offset`` offset nilai dalam query, `default` `0`

      :returns: Array hasil

  .. php:method:: /v1/exchange( $array )

      Melakukan konversi mata uang.

      - ``base`` base currency, `default` `IDR`
      - ``target`` target currency, `default` `USD`
      - ``amount`` nominal yang akan dikonversi, `default` 0
      - ``round`` pembulatan, `default` `0` (`0` | `1`)
      - ``formatted`` human readable, `default` `0` (`0` | `1`)

      :returns: Array dari objek ``rate``.

Example
-------

**GET** ``/v1/gets?base=IDR``

.. code-block:: javascript

      {
        queries: {
          base: "IDR",
          number: 2
        },
        results: [
          {
            sync_date: "2017-05-05 22:30:00",
            base: "IDR",
            name: "British Pound Sterling",
            code: "GBP",
            value: "0.000058130881155744",
            _value_reversed: 17202.5605,
            _value_reversed_round: 17203,
            _value_reversed_formatted: "IDR 17,203"
          },
          {
            sync_date: "2017-05-05 22:29:00",
            base: "IDR",
            name: "Swiss Franc",
            code: "CHF",
            value: "0.000074000619414785",
            _value_reversed: 13513.4004,
            _value_reversed_round: 13513,
            _value_reversed_formatted: "IDR 13,513"
          },
        ]
      }

**GET** ``/v1/exchange?amount=250000&formatted=1&round=1&base=IDR&target=USD``

.. code-block:: javascript

      {
        queries: {
          amount: "250000",
          formatted: "1",
          round: "1",
          base: "IDR",
          target: "USD"
        },
        results: "USD 19"
      }