pertama-tama kita harus mempunya data yang ingin ditampilkan pada database, sebagai contoh dari data saya adalah sebagai berikut
![data](https://github.com/masariuman/catatan_sakti/blob/master/ISI/react1.PNG)

Jangan lupa membuat MODEL dari table yang akan di tampilkan datanya. saya menggunakan table news jadi saya akan membuat model dari tabel news
> php artisan make:model news

setelah itu kita buka file routes > web.php dan kita membuat route untuk menampilkan array dari data kita. disini saya membuat route untuk get news

    Route::get('news',  function(){
	    return App\news::all();
    });
buka pada browser routemu maka akan menampilkan datamu.
![data](https://github.com/masariuman/catatan_sakti/blob/master/ISI/react2.PNG)

sebelum menampilkan data yang kita inginkan, install dulu axios
> npm install axios --save -f

masukkan kode import axios pada file example di atas barisan import
> import axios from  'axios';

kemudian pada atas render, buat fungsi contrusctor untuk membuat variable
	
    constructor()  {
	    super();
    	this.state =  {
	    	news:  []
        }
    }
kemudian kita akan mengambil data pada route /news tadi atau route yang anda gunakan untuk menampilkan data dari db sebelumnya dan akan di simpan kedalam variabel atau array pada constructor. letakkan kode berikut dibawah constructor

    componentDidMount(){
	    axios.get('/news').then(response=>{
		    this.setState({news:response.data});
		}).catch(errors=>{
		    console.log(errors);
	    })
    }
setelah diambil, maka data di tampilkan atau di echo kan ke view dengan kode sebagai berikut

    <div  className="card-body">
	    {
		    this.state.news.map(
			    data  =>
					    <div>
					    <h4>{data.title}</h4>
					    <p>{data.body}</p>
					    </div>
		    )
	    }
    </div>
setelah itu lakukan laravel mix `npm run dev` untuk yang tidak melakukan `npm run watch`. untuk yang melakukan watch selama mengkoding maka tidak perlu melakukan run dev lagi.. maka data akan dapat ditampilkan 
![hasil](https://github.com/masariuman/catatan_sakti/blob/master/ISI/react3.PNG)


kode sementara pada example.js adalah berikut

    import React,  { Component }  from  'react';
    import ReactDOM from  'react-dom';
    import axios from  'axios';
    export  default  class  Example  extends  Component  {
	    constructor()  {
		    super();
		    this.state =  {
			    news:  []
		    }
	    }
	    componentDidMount(){
		    axios.get('/news').then(response=>{
			    this.setState({news:response.data});
		    }).catch(errors=>{
				console.log(errors);
		    })
	    }
	    render()  {
		    return  (
			    <div  className="container">
				    <div  className="row justify-content-center">
					    <div  className="col-md-8">
						    <div  className="card">
							    <div  className="card-header">NEWS LIST</div>
							    <div  className="card-body">
								    {
									    this.state.news.map(
										    data  =>
														    <div>
															    <h4>{data.title}</h4>
															    <p>{data.body}</p>
														    </div>
									    )
								    }
							    </div>
						    </div>
					    </div>
				    </div>
			    </div>
		    );
	    }
    }
    if  (document.getElementById('example'))  {
	    ReactDOM.render(<Example  />, document.getElementById('example'));
    }
