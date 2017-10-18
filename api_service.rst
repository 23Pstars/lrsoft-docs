============
API Services
============

Tim research and development LRsoft telah mengembangkan beberapa API untuk keperluan project. Beberapa API sengaja dibuka ke publik sebagai bahan inspirasi, meskipun beberapa lagi diantaranya tidak benar-benar terbuka (licensed).

Boat Price
==========

API yang dapat menampilkan history harga kapal cepat (fast boat) yang melalui Bali, Lombok, dan pulau-pulau Gili.

Resources
---------
- `LombokFastBoats.com`_
- `BaliFastBoats.com`_
- GiliTickets.com
- GiliBookings.com
- GiliTransfers.com
- GiliBestDeal.com

.. _LombokFastBoats.com: https://www.lombokfastboats.com
.. _BaliFastBoats.com: https://www.balifastboats.com

.. php:class:: https://api.lrsoft.id/boat-price

  Versi 1

  .. php:method:: /v1/gets( $array )

      Menampilkan daftar nilai konversi mata uang.

      - ``fetch_date`` tanggal rate, `default` tanggal saat ini
      - ``depart`` keberangkatan, `default` `empty` (`Lombok` | `Bali` | ...)
      - ``arrive`` tujuan, `default` `empty` (`Lombok` | `Bali` | ...)
      - ``agent`` nama agent, `default` `empty`
      - ``boat`` nama boat, `default` `empty`
      - ``order_by`` mengurutkan daftar, `default` `fetch_date` (`fetch_date` | `depart` | `arrive` | ...)
      - ``order`` mode pengurutan, `default` `DESC` (`DESC` | `ASC`)
      - ``number`` jumlah data, `default` `10`
      - ``offset`` offset nilai dalam query, `default` `0`

      :returns: Array hasil

Example
-------

**GET** ``/v1/gets?depart=Bali&arrive=Lombok&number=2``

.. code-block:: javascript

      {
        queries: {
          depart: "Bali",
          arrive: "Lombok",
          number: 2
        },
        results: [
          {
            fetch_date: "2017-05-06 14:23:32",
            price: "340000",
            depart: "Bali",
            depart_time: "09:30:00",
            arrive: "Lombok",
            arrive_time: "11:00:00",
            agent: "Lombok Fast Boats",
            boat: "Mahi Mahi Dewata",
            _agent_site: "https://www.lombokfastboats.com",
            _boat_logo: "https://api.lrsoft.id/boat-price/assets/images/logos/mahimahi.png",
            _boat_photo: "https://api.lrsoft.id/boat-price/assets/images/boats/mahimahi.jpeg"
          },
          {
            fetch_date: "2017-05-06 14:23:32",
            price: "350000",
            depart: "Bali",
            depart_time: "13:00:00",
            arrive: "Lombok",
            arrive_time: "15:00:00",
            agent: "Lombok Fast Boats",
            boat: "Wahana Gili Ocean",
            _agent_site: "https://www.lombokfastboats.com",
            _boat_logo: "https://api.lrsoft.id/boat-price/assets/images/logos/wahana.png",
            _boat_photo: "https://api.lrsoft.id/boat-price/assets/images/boats/wahana.jpeg"
          }
        ]
      }

Currency Rate
=============

API yang dapat menampilkan nilai konversi dari beberapa mata uang yang umum digunakan di banyak negara.

Resources
---------

Kami menggunakan layanan `Yahoo! Finance`_ untuk mendapatkan nilai konversi mata uang terkini, update setiap hari.

.. _`Yahoo! Finance`: https://finance.yahoo.com/currencies

.. php:class:: https://api.lrsoft.id/currency-rate

  Versi 1

  .. php:method:: /v1/gets( $array )

      Menampilkan daftar nilai konversi mata uang.

      - ``sync_date`` tanggal rate, `default` tanggal saat ini
      - ``base`` dasar nilai konversi, `default` `empty`
      - ``target`` tujuan nilai konversi, `default` `empty`
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
          }
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


IBM Watson
==========

Beberapa API kognitif dari service IBM Watson.

.. php:class:: https://api.lrsoft.id/ibm-watson

  Versi 1

  .. php:method:: /v1/tone-analyzer( $array )

      Menampilkan analisa tone dari konten yang terdapat dalam sebuah website.
      Saat ini baru mendukung site dengan engine ``WordPress`` dan ``Blogger``.

      - ``site`` alamat website yang akan dianalisa (`fully qualified URL`, contoh: ``http://nypost.com``)
      - ``limit`` jumlah post yang akan dianalisa, `default` ``5``

      :returns: JSON

Example
-------

**GET** ``/v1/tone-analyzer?site=http://nypost.com&limit=5``

.. code-block:: javascript

      {
        site: "http://nypost.com",
        limit: 5,
        contents: "Your source for breaking news, news about New York, sports, business, entertainment, opinion, real estate, culture, fashion, and more.Council Speaker Melissa Mark-Viverito publicly called on embattled Correction Commissioner Joe Ponte to resign Wednesday, days after privately sharing that view with Mayor de Blasio. &#8220;I do believe Ponte should step down,&#8221; she told reporters at a City Hall press conference. &#8220;I think he should consider it seriously at this point.&#8221; Mark-Viverito said she made...They’re behind bars, but that doesn’t mean it’s easy to track inmates in the city’s jails. So the Department of Correction is spending $4.5 million to equip them with electronic wristbands that can be monitored in real time. The tracking system was piloted in the fall at one jail and one court facility, and will...Rep. Joseph Crowley, who serves as Queens Democratic leader, is ­using campaign funds to rent office space in a family-owned property outside his district, rec­ords show. Crowley has paid at least $69,700 since 2007 to ­Killean Enterprises LLC, which is controlled by his brother, lobbyist John “Sean” Crowley. As chairman of the House Democratic Caucus,...Wall Street investors ghosted Snap after it reported a larger-than-expected $2.2 billion loss in the first quarter — while ringing up revenue that couldn’t even match the business it drummed up in the fourth quarter. Yes, competing against social media giants like Facebook is proving tough — at least early in Snapchat’s life. It was...",
        results: {
          document_tone: {
            tone_categories: [
                {
                  tones: [
                    {
                      score: 0.205602,
                      tone_id: "anger",
                      tone_name: "Anger"
                    },
                    {
                      score: 0.523796,
                      tone_id: "disgust",
                      tone_name: "Disgust"
                    },
                    {
                      score: 0.120882,
                      tone_id: "fear",
                      tone_name: "Fear"
                    },

      ...


Instagram
=========

Fetching photo dari Instagram.

.. php:class:: https://api.lrsoft.id/instagram

  Versi 1

  .. php:method:: /v1/tag( $array )

      Fetch daftar photo berdasarkan tag.

      - ``tag`` kata kunci tag

      :returns: JSON

  .. php:method:: /v1/user( $user )

      Fetch profil user beserta foto terkini yang dipost.

      - ``user`` username dari akun

      :returns: JSON

Example
-------

**GET** ``/v1/tag?tag=senggigi``

**GET** ``/v1/user?tag=23pstars``


Mail
====

Kirim email menggunakan relay-smtp.

.. php:class:: https://api.lrsoft.id/mail

  Versi 1

  .. php:method:: /v1/send?{$params}

      Kirim email.

      - ``to_email`` alamat email tujuan
      - ``to_name`` nama email tujuan
      - ``from_email`` alamat email pengirim
      - ``from_name`` nama email pengirim
      - ``content`` body email (HTML versi encoded)
      - ``subject`` subjek email
      - ``cc_email`` alamat email CC
      - ``cc_name`` nama email CC
      - ``bcc_email`` alamat email BCC
      - ``bcc_name`` nama email BCC
      - ``reply_to_email`` alamat email untuk tujuan reply
      - ``reply_to_name`` nama email untuk tujuan reply

      :returns: JSON

Example
-------

**GET** ``/v1/send?to_email=zaf@lrsoft.id&to_name=Ahmad%20Zafrullah``
``&from_email=info@lrsoft.org&from_name=LRsoft%20Senggigi``
``&content=Hello%20World&subject=Test%20Mail``

Shipping
========

Biaya pengiriman paket dari ekspedisi JNE, TIKI, dan POS Indonesia.

.. php:class:: https://api.lrsoft.id/shipping

  Versi 1

  .. php:method:: /v1/cities?{$params}
      
      Tampilkan daftar kota-kota di Indonesia.

      - ``city_name`` cari kota berdasarkan nama kota (*optional*)
      - ``province`` cari kota berdasarkan nama provinsi (*optional*)
      - ``order_by`` urutkan berdasarkan field (``city_id`` | ``city_name`` | ``province``) (*optional*)
      - ``order`` model pengurutan (``ASC`` | ``DESC``) (*optional*)
      - ``number`` maksimal data yang ditampilkan, ``-1`` untuk menampilkan semua (*optional*)

      :returns: JSON

  .. php:method:: /v1/cost?{$params}

      Cek biaya kirim.

      - ``origin`` ID kota asal dari ``cities`` (*mandatory*)
      - ``destination`` ID kota tujuan dari ``cities`` (*mandatory*)
      - ``courier_code`` kode kurir (``jne`` | ``tiki`` | ``pos``), *default* ``jne`` (*mandatory*)
      - ``weight`` simulasi berat dari paket (kg) (*optional*)

      :returns: JSON

  .. php:method:: /v1/costs?{$params}

      Cek daftar biaya kirim.

      - ``origin`` ID kota asal dari ``cities`` (*optional*)
      - ``origin_name`` nama kota asal dari ``cities`` (*optional*)
      - ``origin_postal`` kode postal kota asal dari ``cities`` (*optional*)
      - ``destination`` ID kota tujuan dari ``cities`` (*optional*)
      - ``destination_name`` nama kota tujuan dari ``cities`` (*optional*)
      - ``destination_postal`` kode postal kota tujuan dari ``cities`` (*optional*)
      - ``courier_code`` kode kurir (``jne`` | ``tiki`` | ``pos``) (*optional*)
      - ``weight`` simulasi berat dari paket (kg) (*optional*)
      - ``order_by`` urutkan berdasarkan field (``origin`` | ``destination`` | ``courier_code`` | ``courier_service``) (*optional*)
      - ``order`` model pengurutan (``ASC`` | ``DESC``) (*optional*)
      - ``number`` maksimal data yang ditampilkan, ``-1`` untuk menampilkan semua (*optional*)

      :returns: JSON

Example
-------

**GET** ``/v1/cities?city_name=lombok``

.. code-block:: javascript

      {
        status: true,
        cities: [
          {
            city_id: "241",
            province_id: "22",
            province: "Nusa Tenggara Barat (NTB)",
            type: "Kabupaten",
            city_name: "Lombok Utara",
            postal_code: "83711",
            status: "0"
          },
          {
            city_id: "240",
            province_id: "22",
            province: "Nusa Tenggara Barat (NTB)",
            type: "Kabupaten",
            city_name: "Lombok Timur",
            postal_code: "83612",
            status: "0"
          },
          {
            city_id: "239",
            province_id: "22",
            province: "Nusa Tenggara Barat (NTB)",
            type: "Kabupaten",
            city_name: "Lombok Tengah",
            postal_code: "83511",
            status: "0"
          },
          {
            city_id: "238",
            province_id: "22",
            province: "Nusa Tenggara Barat (NTB)",
            type: "Kabupaten",
            city_name: "Lombok Barat",
            postal_code: "83311",
            status: "0"
          }
        ]
      }

**GET** ``/v1/cost?origin=501&destination=501&courier_code=jne&weight=10``

.. code-block:: javascript

      {
        status: true,
        cost: {
          origin: "501",
          destination: "501",
          courier_code: "jne",
          courier_service: "CTC",
          cost: "5000",
          delivery: "1-2",
          note: "",
          _cost_total: "50000"
        }
      }

**GET** ``/v1/costs?origin_name=Yogyakarta&destination_name=Mataram&courier_code=jne``

.. code-block:: javascript

      {
        queries: {
          origin_name: "Yogyakarta",
          destination_name: "Mataram",
          courier_code: "jne"
        },
        results: [
          {
            origin: "501",
            destination: "276",
            courier_code: "jne",
            courier_service: "OKE",
            cost: "30000",
            delivery: "4-5",
            note: "",
            _cost_total: "30000",
            _cost_total_formatted: "30,000",
            _origin_name: "Yogyakarta",
            _destination_name: "Mataram",
            _origin_postal: "55222",
            _destination_postal: "83131"
          },
          {
            origin: "501",
            destination: "276",
            courier_code: "jne",
            courier_service: "REG",
            cost: "35000",
            delivery: "2-3",
            note: "",
            _cost_total: "35000",
            _cost_total_formatted: "35,000",
            _origin_name: "Yogyakarta",
            _destination_name: "Mataram",
            _origin_postal: "55222",
            _destination_postal: "83131"
          },
          {
            origin: "501",
            destination: "276",
            courier_code: "jne",
            courier_service: "YES",
            cost: "58000",
            delivery: "1-1",
            note: "",
            _cost_total: "58000",
            _cost_total_formatted: "58,000",
            _origin_name: "Yogyakarta",
            _destination_name: "Mataram",
            _origin_postal: "55222",
            _destination_postal: "83131"
          }
        ]
      }