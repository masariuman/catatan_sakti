pertama-tama install lara project terlebih dahulu

> php composer.phar create-project --prefer-dist laravel/laravel reactlara

setelah itu masuk ke dalam folder aplikasi dan mengidentifikasi react
> php artisan preset react

setelah itu install react dengan cara
> npm install && npm run dev

jangan lupa untuk mengedit file env untuk database dan menjalankan laravel terlebih dahulu
> php artisan serve --port=9696

setelah menginstall react maka akan terdapat file js didalam resource dan didalamnya terdapat file app.js, bootstrap.js dan folder components yang berisikan example.js. disini kita akan membuat view pada reactlara.
sebelum kita membuat view pada bagian js, pertama-tama kita arahkan view welcome atau view dari route {/} ke arah js component yang ingin di jadikan view pada route tersebut, pada hal ini kita gunakan contoh ke arah example.js. buka file welcome.blade.php pada resource > views. berikut kode dari welcome.blade.php.

    <!doctype  html>
    <html lang="{{ str_replace('_', '-', app()->getLocale()) }}">
    <head> 
    <meta  charset="utf-8">
    <meta  name="viewport"  content="width=device-width, initial-scale=1">
    <title>Laravel</title>
    <!-- Fonts -->
    <link  href="https://fonts.googleapis.com/css?family=Nunito:200,600"  rel="stylesheet">
    <!-- Styles -->
    <style>
    html,  body  {
    background-color:  #fff;
    color:  #636b6f;
    font-family:  'Nunito',  sans-serif;
    font-weight:  200;
    height:  100vh;
    margin:  0;
    }
    .full-height  {
    height:  100vh;
    }
    .flex-center  {
    align-items:  center;
    display:  flex;
    justify-content:  center;
    }
    .position-ref  {
    position:  relative;
    }
    .top-right  {
    position:  absolute;
    right:  10px;
    top:  18px;
    }
    .content  {
    text-align:  center;
    }
    .title  {
    font-size:  84px;
    }
    .links  >  a  {
    color:  #636b6f;
    padding:  0  25px;
    font-size:  13px;
    font-weight:  600;
    letter-spacing:  .1rem;
    text-decoration:  none;
    text-transform:  uppercase;
    } 
    .m-b-md  {
    margin-bottom:  30px;
    }
    </style>
    </head>
    <body>
    <div  class="flex-center position-ref full-height">
    @if (Route::has('login'))
    <div  class="top-right links">
    @auth
    <a  href="{{ url('/home') }}">Home</a>
    @else
    <a  href="{{ route('login') }}">Login</a>
    @if (Route::has('register'))
    <a  href="{{ route('register') }}">Register</a>
    @endif
    @endauth
    </div>
    @endif
    <div  class="content">
    <div  class="title m-b-md">
    Laravel
    </div>
    <div  class="links">
    <a href="https://laravel.com/docs">Docs</a>
    <a  href="https://laracasts.com">Laracasts</a>
    <a  href="https://laravel-news.com">News</a>
    <a  href="https://blog.laravel.com">Blog</a>
    <a  href="https://nova.laravel.com">Nova</a>
    <a  href="https://forge.laravel.com">Forge</a>
    <a  href="https://github.com/laravel/laravel">GitHub</a>
    </div>
    </div>
    </div>
    </body>
    </html>
Hapus tag dan isi `<style> </style>` , isi dari `<body> </body>` dan fonts dan akan menjadi seperti berikut.

    <!doctype  html>
	<html  lang="{{ str_replace('_', '-', app()->getLocale()) }}">
	    <head>
		    <meta  charset="utf-8">
		    <meta  name="viewport"  content="width=device-width, initial-scale=1">
		    <title>Laravel</title>
	    </head>
	    <body>
	    </body>
    </html>
masukkan css, script js dan div untuk dipakai react seperti berikut

    <!doctype  html> 
    <html  lang="{{ str_replace('_', '-', app()->getLocale()) }}">
	    <head>
		    <meta  charset="utf-8">
		    <meta  name="viewport"  content="width=device-width, initial-scale=1">
		    <title>Laravel</title>
		    <link  rel="stylesheet"  href="css/app.css">
	    </head>
	    <body>
		    <div  id="example"></div>
		    <script  src="js/app.js"></script>
	    </body>
    </html>
dapat dilihat diatas saya menambahkan `<link rel="stylesheet" href="css/app.css">` , `<div id="example"></div>` dan `<script src="js/app.js"></script>`
buka kembali php artisan serve untuk melihat perubahan, view yang ditampilkan berada pada resource > js > component > example. dan akan menghasilkan view yang berbeda dari laravel pada umumnya.
