pertama tama kita buat form nya terlebih dahulu pada example.js

    <form  onSubmit={this.handleSubmit}>
	    Title: <input  onChange={this.handleChangeTitle}  value={this.state.title}></input>
	    Body: <textarea  onChange={this.handleChangeBody}  value={this.state.body}></textarea>
	    <button  type="submit">SUBMIT</button>
    </form>
setelah itu kita definisakan variable untuk title dan body pada constructor didalam state

    this.state =  {
	    news:  [],
	    title:'',
	    body:''
    }
kemudian kita mendefinisakan handleChange dibawah state

    this.handleChangeTitle =  this.handleChangeTitle.bind(this);
    this.handleChangeBody =  this.handleChangeBody.bind(this);
    this.handleSubmit =  this.handleSubmit.bind(this);
setelah itu kita buat fungsi handlechange dan submit utk aksi dari form

    handleChangeTitle(e)  {
	    this.setState({
		    title:e.target.value,
	    })
    }
    handleChangeBody(e)  {
	    this.setState({
		    body:e.target.value,
	    })
    }
    handleSubmit(e)  {
	    e.preventDefault();
	    axios.post('addNews',  {
		    title:this.state.title,
		    body:this.state.body
	    }).then(res=>{
		    console.log(res.data);
		    this.setState({
			    news:res.data
		    });
	    });
    }
setelah itu membuat controller untuk mengatasi create
`php artisan make:controller newsController --resource`
buka route web.php dan tambahkan 

> Route::post('addNews','newsController@store');

buka file newsController pada app > http > controller dan tambahkan `use DB;` dan `use App\news;` dibawah `use Illuminate\Http\Request;` dan tambahkan kode didalam function store.

    $title =  $request->title;
    $body =  $request->body;
    $add =  DB::table('news')->insert([
	    'title'=>$title,
	    'body'=>$body
    ]);
    if($add){
	    return  news::orderBy('id','DESC')->get();
    }
DAN  MENG !! kode untuk insert data sudah selesai, silahkan lakukan laravel mix `npm run dev` kalau tidak  melakukan watch selama pengkodean. dan buka apps untuk mencoba.


kode akhir dari example.js

    import React,  { Component }  from  'react';
    import ReactDOM from  'react-dom';
    import axios from  'axios';
    export  default  class  Example  extends  Component  {
	    constructor()  {
		    super();
		    this.state =  {
			    news:  [],
			    title:'',
			    body:''
		    }
		    this.handleChangeTitle =  this.handleChangeTitle.bind(this);
		    this.handleChangeBody =  this.handleChangeBody.bind(this);
		    this.handleSubmit =  this.handleSubmit.bind(this);
	    }
	    handleChangeTitle(e)  {
		    this.setState({
			    title:e.target.value,
		    })
	    }
	    handleChangeBody(e)  {
		    this.setState({
			    body:e.target.value,
		    })
	    }
	    handleSubmit(e)  {
		    e.preventDefault();
		    axios.post('addNews',  {
			    title:this.state.title,
			    body:this.state.body
		    }).then(res=>{
			    console.log(res.data);
			    this.setState({
				    news:res.data
			    });
		    });
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
							    <form  onSubmit={this.handleSubmit}>
								    Title: <input  onChange={this.handleChangeTitle}  value={this.state.title}></input>
								    Body: <textarea  onChange={this.handleChangeBody}  value={this.state.body}></textarea>
								    <button  type="submit">SUBMIT</button>
							    </form>
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
