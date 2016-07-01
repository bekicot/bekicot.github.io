---
layout: post
title: "Ruby on Rails Versi 5 Telah Rilis, Apa Aja Yang Baru ?"
date: 2016-07-02T04:01:18+07:00
---

Kemarin, Ruby On Rails 5 baru saja di rilis. Setelah 6 bulan penantian, tepatnya desember tahun lalu, akhirnya versi stabil dari Rails 5 diluncurkan kemarin, 30 juni 2016. Banyak sekali penambahan feature baru yang sangat bermanfaat bagi pengembangan saas yang di masukan dalam rilis kali ini. Berikut adalah perubahan terbesar dari Rails 5.


Rails API
---------
Sebetulnya feature ini telah di canangkan sejak 2012 dan di implementasikan pada salah satu versi [Rails 4 yang tidak di rilis](https://github.com/rails/rails/commit/6db930cb5bbff9ad824590b5844e04768de240b1). Dengan fitur ini, kita dapat membuat Rails berada dalam mode API, dengan mengurangin dependency yang tidak kita gunakan jika kita hanya mersponse dengan JSON. 

Kita bisa membuat aplikasi baru dengan API mode hanya dengan mengeksekusi

`rails new my_api --api`


Action Cable
------------

Action Cable adalah framework untuk menggunakan web socket di rails. Web socket adalah feature yang bisa di gunakan untuk membuat real time aplication seperti chatting, notifikasi, dan async background task. Action Cable menyediakan semua hal yang di butuhkan untuk membuat aplikasi yang menggunakan web socket mulai dari Channels yang di sediakan di rails, hingga javascript yang bisa di gunakan di komputer client. 


Info lebih lanjut [Rails Announcement](http://weblog.rubyonrails.org/2016/6/30/Rails-5-0-final/)
