# First Installation
bikin project laravel
```
composer create-project --prefer-dist laravel/laravel blog
```

---

sebelum npm install, composer require dulu untuk auth, pakai inertia /liveware
```composer require laravel/jetstream```

```php artisan jetstream:install livewire```
atau
```php artisan jetstream:install inertia```

```sudo xcode-select --reset```
---

masuk ke folder project dan jalankan 
```npm install```

---

atur db di .env dan lakukan ```php artisan migrate```

---

install react pada laravel
```npm i react```

---

install react-dom pada laravel
```npm i react-dom```

---

rename extensi file js react ke .jsx

---

jalankan ```npm run dev```

---

atur templade blade masukkan script app.js (defer) ```<script src="/js/app.js" defer></script>``` dan tambahkan div id root ```<div id="root"></div>```

---

pada app.jsx untuk template dasar masukkan kode berikut
```js
require('./bootstrap');

import React, { Component } from 'react';
import ReactDOM from "react-dom";

ReactDOM.render(
        <div>
            <p>test</p>
            <p>BERHASIL !!</p>
        </div>,

    document.getElementById("root")
);
```

---
## Instalasi Aplikasi ReactJS pada Laravel 8.* Selesai !!!

---

# React Router Dom
jalankan ```npm install react-router-dom```

---

import react router dengan menambahkan kode import diatas file sebagai berikut.
```js
import {
  BrowserRouter as Router,
  Switch,
  Route,
  Link
} from "react-router-dom";
```

---

atur route nya seperti pada [dokumentasi](https://reactrouter.com/web/guides/quick-start)

---

masukkan kode berikut di route laravel agar route dialihkan ke react-route.
```js
Route::any('{all}', function () {
        return view('hiyaa');
    })
    ->where(['all' => '.*']);
```

---

### SELESAI !!!

----

# Route Controller laravel 8

---

pada file RouteServiceProvider, hilangkan komen / uncomment code ```protected $namespace = 'App\\Http\\Controllers';```

---

# Model Not Found Laravel 8

---

kalau copy paste dari model dibawah laravel 8, jangan lupa untuk namespace di atasnya ditambahkan ```App\Model```

---

# Axios

---

install axios terlebih dahulu dengan kode
```npm install axios```

---

# summernote
1. npm install react-summernote
2. pada baris 2 webpack masukkan ```const webpack = require("webpack");```
3. mix nya diganti jadi
``` js
mix.react('resources/js/app.jsx', 'public/js')
    .postCss('resources/css/app.css', 'public/css', [
        //
    ])
    .webpackConfig({
        plugins: [
            new webpack.ProvidePlugin({
                $: "jquery",
                jQuery: "jquery"
            })
        ]
    });
```
    
    
4. install dependencies summernote yang dibutuhkan. contohnya dibawah ini. yang dibawah ini belm install react dan react-dom.
``` js
npm WARN react-summernote@2.0.2 requires a peer of bootstrap@^3.3.6 but none is installed. You must install peer dependencies yourself.
npm WARN react-summernote@2.0.2 requires a peer of jquery@^2.2.0 || ^3.0.0 but none is installed. You must install peer dependencies yourself.
npm WARN react-summernote@2.0.2 requires a peer of react@^15.0.0 but none is installed. You must install peer dependencies yourself.
npm WARN react-summernote@2.0.2 requires a peer of react-dom@* but none is installed. You must install peer dependencies yourself.
```

5. contoh app.js untuk summernote
``` js
require('./bootstrap');

import React, { Component } from 'react';
import ReactDOM from "react-dom";
import $ from 'jquery';
import ReactSummernote from 'react-summernote';
import 'react-summernote/dist/react-summernote.css'; // import styles
import 'react-summernote/lang/summernote-ru-RU'; // you can import any other locale

import 'bootstrap/js/modal';
import 'bootstrap/js/dropdown';
import 'bootstrap/js/tooltip';
// import 'bootstrap/dist/css/bootstrap.css';

ReactDOM.render(
        <div>
            <ReactSummernote
                value="Default value"
                options={{
                lang: 'ru-RU',
                height: 350,
                dialogsInBody: true,
                toolbar: [
                    ['style', ['style']],
                    ['font', ['bold', 'underline', 'clear']],
                    ['fontname', ['fontname']],
                    ['para', ['ul', 'ol', 'paragraph']],
                    ['table', ['table']],
                    ['insert', ['link', 'picture', 'video']],
                    ['view', ['fullscreen', 'codeview']]
                ]
                }}
            />
        </div>,

    document.getElementById("root")
);
```

---

copy boostrap.css di ```node_module/bootstrap/dist/css/bootstrap.css``` ke public/css terus letakkan ```<link href="/css/bootstrap.css" rel="stylesheet">``` di paling atas css

---

#### SELESAI !!!

---

# EnjoyHint

---

letakkan folder enjoyhint di public

---

tambahkan kode berikut sebagai js dan css

```js
<link href="/enjoyhint/enjoyhint.css" rel="stylesheet">

<script src="https://code.jquery.com/jquery-3.5.1.js" integrity="sha256-QWo7LDvxbWT2tbbQ97B53yJnYU3WhH/C8ycbRAkjPDc=" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/kineticjs/5.2.0/kinetic.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-scrollTo/2.1.2/jquery.scrollTo.min.js"></script>
<script src="/enjoyhint/enjoyhint.min.js"></script>
```

---

masukkan code jquery nya di component did mount seperti berikut

```js
    componentDidMount() {
        $('#petunjuk').on('click',function() {
            //initialize instance
            var enjoyhint_instance = new EnjoyHint({});

            //simple config.
            //Only one step - highlighting(with description) "New" button
            //hide EnjoyHint after a click on the button.
            var enjoyhint_script_steps = [
            {
                'next #buttonTambahModal' : 'Click the "New" button to start creating your project'
            }
            ];

            //set script config
            enjoyhint_instance.set(enjoyhint_script_steps);

            //run Enjoyhint script
            enjoyhint_instance.run();
        });
    }
```

---

jangan lupa install jquery di react, mirip dengan cara summernote

---

### selesai

---

# SweetAlert

---

```js
npm install sweetalert --save
```

kemudian

```js
import swal from 'sweetalert';
```

kemudian

```js
swal("Error!", "Terdapat Masalah, Silahkan Hubungi Admin!", "error");
```

---
