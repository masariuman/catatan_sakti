1. bikin project laravel
2. masuk ke folder project dan jalankan "npm install"
3. npm i react
4. npm i react-dom



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
