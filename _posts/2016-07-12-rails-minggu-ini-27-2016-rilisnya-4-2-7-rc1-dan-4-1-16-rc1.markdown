---
layout: post
title: "Rails Minggu Ini (27-2016) - Rilisnya 4.2.7.rc1 Dan 4.1.16.rc1"
date: 2016-07-12T11:56:00+07:00
---

Hallo Semua,
Sebetulnya this week in rails jumat kedua bulan juli sudah release sejak sabtu pagi minggu lalu, namun karna saya sedang libur lebaran, jadi proses translatenya ngaret dan baru selesai hari ini :).

Edisi kali ini di kompilasi oleh [Jon](https://twitter.com/jonatack) (Juan El Badido). Dia meringkas perubahan pada Rails 2 minggu terakhir.

Headline
--------
### Contributors

Ada sekitar [38 orang](http://contributors.rubyonrails.org/contributors/in-time-window/20160702-201607008) yang berkontribusi untuk rails, termasuk 8 orang yang baru pertama kali memberikan kontribusi. Ini artinya 20 % dari commiters, merupakan orang baru.

### Rails 4.2.7.rc1 dan 4.1.16.rc1 telah rilis

2 rilis candidate telah di publikasikan 10 hari lalu. Final release dari rails 4.1.16 seharusnya release secepatnya jika tidak di temukan adanya regresi. Mungkin aja ini rilis terakhir dari rails 4.1.x, jadi upgrade rails mu ke rails 5 untuk mendapatkan support yang lebih panjang.


### Sintax baru untuk Action View tag helpers

Feature ini di bangun berdasar [proposal](https://github.com/rails/rails/issues/25195) yang di buat DHH. Sintax baru ini mendukung HTML5 markup dan menghindari parameter posisi. Pull request (25289) telah di merge dan kita bisa lihat diskusinya secara seksama [di sini](https://github.com/rails/rails/pull/25289)

### Update di Rails Guides

Banyak dokumentasi baru di tambahkan dalam 2 minggu terakhir, termasuk finalisasi [Rails Testing Guides](http://edgeguides.rubyonrails.org/testing.html) dan dokumentasi update untuk feature dan pattern baru di Rails 5.

Peningkatan
-----------
### [Stack Trace yang lebih rapih](https://github.com/rails/rails/pull/25222)
Di buat untuk Rails 5.1, [PR](https://github.com/rails/rails/pull/25343) ini merapihkan stack trace yang panjang dan belibet menjadi lebih simple dan fokus terhadap error yang di raise. 

### [Update Action View tag helpers attributes](https://github.com/rails/rails/pull/25555)
Commit ini menambahkan boolean attributes untuk Action View tag helpers sesuai dengan [Spesifikasi w3.org](https://www.w3.org/TR/html51/single-page.html). Mengganti `autobuffer` menjadi `preload` dan menghapus `pubdate`.

### [Raise Error dalam nested time travel helpers](https://github.com/rails/rails/pull/24890)
Nested time travel calss dalam test mungkin membingungkan dalam time subbing. Untuk mengurangi kebingungan dan rails pun tidak merekomendasikan nested time travel, kini Rails akan me raise error.

Bug Fix
-------

### [Menggunakan timezone yang sesuai dalam parsing tanggal dalam json](https://github.com/rails/rails/pull/23011)
Sesuai dengan format ISO 8601 format tanggal tanpa Z seharusnya di parse dengan waktu server yang memparse, namun hingga commit ini di merge, Rails masih menganggap tanggalnya merupakan tanggal di UTC. Solusi yang di gunakan adalah dengan memparse Time menggunakan timezone yang di set di dalam application config.
Perubahan juga di porting ke Rails 5.0-stable.

### [Routes yang menggunakan option `as` sekarang bisa di gunakan di GET request](https://github.com/rails/rails/pull/25435)
Sekarang bisa menambahkan opsi pada akhir URL url (.json, .xml) ketimbang menggunakan parameter. Jika di review dengan seksama pada [PR](https://github.com/rails/rails/pull/25435) terdapat diskusi terhadap performance.

### [Fix Race Condition pada websocket stream writes](https://github.com/rails/rails/pull/25624)
Kini ActionCable::ConnectionStream aman terhadap concurent write ke konesi websocket yang berasal dari multi thread. Juga telah di persiapkan untuk minor release pada Rails 5.0.0

### [Menutup Hijacked socket I/O setelah di gunakan](https://github.com/rails/rails/pull/25615)
Issue ini terjadi ketika menggunakan web socket dan merefresh browser beberapa kali. Seharusnya koneksi websocket hanya ada 1 karna hanya 1 browser yang mengaksesnya, tapi jumlah sesi terbuka terus bertambah. [PR](https://github.com/rails/rails/pull/25615) telah di merge dan di backport ke Rails 5.0.0

### [Fix tidak memberikan etag value baru  ketika menambahkan `implicitly-rendered` template](https://github.com/rails/rails/pull/25546)
Ketika template sudah di modifikasi, seharusnya response tidak memberikan status 301, namun status 200. Kini response menghasilkan ETag baru, error telah di backport ke  5-0-stable.

### [Fix Type::Date#serialize tidak mengcast nilai menjadi date object](https://github.com/rails/rails/pull/25364)
Sebelumnya `Type::Date#serialize` tidak mengcast value menjadi date object. Seharusnya di jadikan date object agar tidak terjadi kesalahan ketika `find` column date (pada database).

Terbaru
-------

### [Middleware baru untuk debugging reloading/executing deadlocks](https://github.com/rails/rails/pull/25344)
Menambahkan feature baru untuk diagnosa deadlocks

### [Memanggil `rake notes` untuk direktori lain](https://github.com/rails/rails/pull/25692)
Sebelumnya, SourceAnnotationExtractor tidak bisa mengextract notes dari deriektori selain direktori yang sudah ditentukan (app, config, db, lib, test). Kini kita bisa menambahkan direktori baru dengan `SourceAnnotationExtractor::Annotation.register_directories("spec", "other_dir")`


Terima Kasih
============
Phew, akhirnya. Di edisi kini banyak sekali penambahan baru agar lebih mudah di pahami. Jadi jika ada kesalahan, kemungkinan kesalahan itu ada pada saya, bukan pada edisi [orisinil](https://rails-weekly.ongoodbits.com/2016/07/08/this-wild-week-in-rails-rails-4-2-7-4-1-16-new-tag-helpers-syntax-and-more)

Bantu saya translate di [github](https://github.com/bekicot/bekicot.github.io)
