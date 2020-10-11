# First Installation
bikin project laravel
```
composer create-project --prefer-dist laravel/laravel blog
```

---

masuk ke folder project dan jalankan 
```npm install```

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

# summernote
1. npm install react-summernote
2. pada baris 2 webpack masukkan "const webpack = require("webpack");"
3. mix nya diganti jadi
``` js
mix.react("resources/js/app.js", "public/js")
    .sass("resources/sass/app.scss", "public/css");
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
import 'bootstrap/dist/css/bootstrap.css';

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
