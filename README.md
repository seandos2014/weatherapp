# weatherapp
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <meta http-equiv="Content-Type">
    <title>Weather App</title>
    <link type="text/css" rel="stylesheet" href="index.css" >
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
    
    <style>
        /*========= Shared styles ==================*/
body{
background-color: #08758A;
}

.app-row{
    width: calc(100%-10px);
    margin: 5px;
}

.app-row:after{
    width:100%;
    height:100%;
    content: "";
    display:table;
    clear: both;
}

.app-col{
    float:left;
    margin-top: 5px;;
    width: 33.33%;
    height: 100%;
    padding:10px;
    color: gray;
    background-color: whitesmoke;
    text-align: center;
    cursor: pointer;
    list-style-type: none;
}

.active-nav{
 color:firebrick;
 border-bottom: 5px solid firebrick;
}

.non-active-nav{
 color:gray;
 text-decoration: none;   
}

@media screen and (max-width:660px){
    .app-col{
        background-color: white;
        margin-top: 5px;
        padding: 10px;
        width: 90%;
        overflow-x: auto;
        height: 30px;
        display: block;
        padding: 10px;
        border: 2px solid #08758A;
        margin-left: 0;
        list-style-type: none;

    }
    .app-col:active{
        color:firebrick;
        border-bottom: 5px solid firebrick;
       }
       
       .non-active-nav{
        color:gray;
        text-decoration: none;   
       }
       
}

#page{
width: 100%;
height: 100%;
position : relative;
overflow-y: auto;
}

#location{
position: absolute;
right:0;
top:0;
left:calc(50%-10px);
right:10px;
width: 40%;
height: 100%;
background-color: white;
border: 2px solid gray;
display: none;
overflow-x:hidden;
overflow-y:auto;
text-align: justify;
}

.search-label{
background-color: #08758A;
color:white;
font-size: 18px;
text-align: center;
font-weight: bold;
}

.cities{
font-size: 15px;
color: #08758A;
padding:5px;
width:100%;
margin: 0px;
text-align: center;
border: 1px solid gray;
}

.div-block-top{
background-color: white;
margin: 5px;
padding: 10px;
width: calc(100%-10px);
height: 40%;
border: 2px solid light-gray;
}

.div-block-bottom{
background-color: white;
margin: 5px;
padding: 10px;
width: calc(100%-10px);
height: 60%;
border: 2px solid light-gray;
overflow-y: auto;
}

.d_heading .t_heading{
margin-top: 20px;
font-size:20px;
font-weight: bold;
text-decoration: black;
}

/*=========== Timely Updates =============*/
.t_row{
width: calc(100%-10px);
margin: 5px;
}

.t_row:after{
content: "";
display: table;
clear: both;
}

.t_col{
float: left;
width: 25%;
text-align: center;
}

.t_temp{
content: "\00B0";
margin-top: 10px;
font-size:12px;
font-weight: bold;
text-align: center;
}

.t_rain{
margin-top: 10px;
font-size:12px;
color: #08758A
}

.t_icon{
margin-top: 10px;
width: 20px;
height: 20px;
}

.t_time{
margin-top: 10px;
font-size:12px;
}



/* ========== Daily Updates ================*/
.d_col{
width: 100%;
max-height: 60%;
}

.d_row{
width: 100%;
height: 20%;
display: flex;
justify-content: center;
text-align: center;
}

.d_span1{
width: 25%;
float:left;
display: flex;
justify-content: center;
text-align: center;
margin-top:20px;
}

.d_span2{
width: 50%;
float:left;
}

.d_span3{
width: 25%;
float:left;
margin-top:20px;
}

.d_icon{
margin-top: 10px;
width: 20px;
height: 20px;
}

.d_date{
content: "\00B0";
margin-top: 20px;
font-size:12px;
font-weight: bold;
text-align: center;
}

.d_desc{
content: "\00B0";
margin-top: 20px;
font-size:12px;
text-align: center;
}

.d_temp{
content: "\00B0";
margin-top: 20px;
font-size:12px;
font-weight: bold;
text-align: center;
}

    </style>
    <style>
      * {box-sizing: border-box;}
      
      body {
        margin: 0;
        font-family: Arial, Helvetica, sans-serif;
      }
      
      .topnav {
        height: 60px;
        width: 100%;
        margin-left: 2px;
        margin-right: 2px;
        margin-top: 0px;
        margin-bottom: 0px;
        overflow: hidden;
        background-color: #08458A;
        color: white;
      }
      
      .topnav a {
        float: left;
        display: block;
        color: white;
        text-align: center;
        padding: 14px 16px;
        text-decoration: none;
        font-size: 18px;
      }
      
      .topnav input[type=text] {
        padding: 6px;
        margin-top: 8px;
        font-size: 17px;
        border: none;
      }
      
      .topnav .search-container button {
        float: right;
        padding: 5px;
        margin-top: 5px;
        margin-right: 2px;
        background: #ddd;
        font-size: 12px;
        border: none;
        cursor: pointer;
      }
      
    
      .search-box{
        float:right;
        margin-top: 5px;
      }
      
      @media screen and (max-width: 600px) {
        .topnav .search-container {
          float: none;
        }
        .topnav a, .topnav input[type=text], .topnav .search-container button {
          float: none;
          display: block;
          text-align: left;
          width: 100%;
          margin: 0;
          padding: 14px;
        }
        .topnav input[type=text] {
          border: 1px solid #ccc;  
        }
      }
      </style>
      
</head>
<body>
       <div class="topnav">
          <a class="active" href="#name">Sample Weather</a>
          <a style="float:right;"><i class="fa fa-search" onclick="handleHide()"></i></a>
       </div>

    <div class="app-row">
        <a class="app-col active-nav" href="#" onclick="handle_col1()"></a>
        <a class="app-col" href="#" onclick="handle_col2()"></a>
        <a class="app-col" href="#" onclick="handle_col3()"></a>
    </div>
                      <div id="page"> 
                          <div class="div-block-top">
                             <form action="#">
                              <span class="search-span" style="display: none;"> 
                              <button class="search-box" style="background-color: green;color: white;" onclick="handleSearch()">Go</button>
                              <input class="search-box" type="text" placeholder="you can also search city..." id="search_value"/>
                              </span>
                              </form>
                             <p class="t_heading"></p>
                            <div class="t_row"><div class="t_col">


                     <p class="t_temp"></p>
                     <p class="t_rain"></p>
                     <img class="t_icon" alt="icon"/>
                     <p class="t_time"></p>
                   </div>

                   <div class="t_col">
                     <p class="t_temp"></p>
                     <p class="t_rain"></p>
                     <img src="" class="t_icon" alt="icon"/>
                     <p class="t_time"></p>
                   </div>

                   <div class="t_col">
                    <p class="t_temp"></p>
                    <p class="t_rain"></p>
                    <img src="" class="t_icon" alt="icon"/>
                    <p class="t_time"></p>
                   </div>

                   <div class="t_col">
                    <p class="t_temp"></p>
                    <p class="t_rain"></p>
                    <img src="" class="t_icon" alt="icon"/>
                    <p class="t_time"></p>
                  </div>
           </div>

       

       </div>
       
       
       <div class="div-block-bottom">
        <p class="d_heading"></p>
        <div class="d_col">
       
          <div class="d_row">
          <span class="d_span1">
            <img class="d_icon"/>
          </span>
          <span class="d_span2">
             <p class="d_date"></p>
             <p class="d_desc"></p>
          </span>
          <span class="d_span3">
             <p class="d_temp"></p>
          </span>
        </div>

        <div class="d_row">
          <span class="d_span1">
            <img class="d_icon"/>
          </span>
          <span class="d_span2">
             <p class="d_date"></p>
             <p class="d_desc"></p>
          </span>
          <span class="d_span3">
             <p class="d_temp"></p>
          </span>
        </div>
       
        <div class="d_row">
          <span class="d_span1">
            <img class="d_icon"/>
          </span>
          <span class="d_span2">
             <p class="d_date"></p>
             <p class="d_desc"></p>
          </span>
          <span class="d_span3">
             <p class="d_temp"></p>
          </span>
        </div>
       
        <div class="d_row">
          <span class="d_span1">
            <img class="d_icon"/>
          </span>
          <span class="d_span2">
             <p class="d_date"></p>
             <p class="d_desc"></p>
          </span>
          <span class="d_span3">
             <p class="d_temp"></p>
          </span>
        </div>
       
        <div class="d_row">
          <span class="d_span1">
            <img class="d_icon"/>
          </span>
          <span class="d_span2">
             <p class="d_date"></p>
             <p class="d_desc"></p>
          </span>
          <span class="d_span3">
             <p class="d_temp"></p>
          </span>
        </div>
       

       </div>


      </div>


      <div>
        <span><p class="created-by" style="font-size: 12px;color: white;text-align: center;">Powered by Ade Dosunmu &#169 2024</p></span>
      </div>

<noscript>Please Enable JavaScript for ths page to work properly</noscript>
<script src="index.js"></script>
<script>
  // API Fetch Initial Variables
const ria_api_key = "482944e26d320a80bd5e4f23b3de7d1f";
const my_api_key = "0f625f5b0482a767f98983091bdac3d4";
const http = "http://";
function fetchData(city){
const forecast_url = `${http}api.openweathermap.org/data/2.5/forecast?q=${city}&appid=${my_api_key}`;
// using AbortController to detect anormality during api fetch
const controller = new AbortController();
const signal = controller.signal;var isOk;
const fetchPromise = fetch(forecast_url, { signal }); // api for the get request
  // Timeout after 5 seconds
const timeoutId = setTimeout(() => {
controller.abort(); // Abort the fetch request
console.log('Fetch request timed out');
}, 5000);  
// Handle the fetch request
fetchPromise
.then(response => {
  // Check if the request was successful
  if (!response.ok) { isOk=0;
  throw new Error('Network response was not ok');
  } 
  // Parse the response as JSON
  document.getElementsByClassName('t_heading')[0].innerText = "Next Hours";
  document.getElementsByClassName('d_heading')[0].innerText = "Next 5 days";
  return response.json();
})  // data munging and wrangling begins
.then(data => {isOk=JSON.stringify(data.list.length);
  try{
    for (i=0; i<4; i++){ 
      document.getElementsByClassName("t_temp")[i].innerText=parseInt(JSON.parse(JSON.stringify(data.list[i])).main.temp)-273+String.fromCharCode(176);
      document.getElementsByClassName("t_rain")[i].innerText=parseInt(JSON.parse(JSON.stringify(data.list[i])).pop)+String.fromCharCode(37);
      document.getElementsByClassName("t_icon")[i].src=get_icon(JSON.parse(JSON.stringify(data.list[i])).weather[0].icon);
      document.getElementsByClassName("t_time")[i].innerText=getTm(JSON.parse(JSON.stringify(data.list[i])));
      }var k=0;
    for (j=0; j<5; j++){
      document.getElementsByClassName("d_icon")[j].src=get_icon(JSON.parse(JSON.stringify(data.list[k])).weather[0].icon);
      document.getElementsByClassName("d_date")[j].innerText=getDt(JSON.parse(JSON.stringify(data.list[k])));  
      document.getElementsByClassName("d_desc")[j].innerText=JSON.parse(JSON.stringify(data.list[k])).weather[0].description;  
      document.getElementsByClassName("d_temp")[j].innerText=(parseInt(JSON.parse(JSON.stringify(data.list[k])).main.temp_max)-273)+String.fromCharCode(176)+" "+(parseInt(JSON.parse(JSON.stringify(data.list[k])).main.temp_min)-273)+String.fromCharCode(176); 
      k=k+8;}
    } catch (error) {
      return;
    }
    })
.catch(error => {
    // Handle any errors that occurred during the fetch
    console.error('Fetch error:', error);
  })
.finally(() => {
    clearTimeout(timeoutId);return isOk; // Clear the timeout
  }); 
}

const daysOfWeek = ["Sun", "Mon", "Tue", "Wed", "Thur", "Fri", "Sat"]
const month = ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"];
const get_full_month = ["January", "Febuary", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
const get_icon = (icon) => { return `http://openweathermap.org/img/w/${icon}.png`; }; // get icon url

//format the time
const format_time = (time) => {
var ff = parseInt(time.substring(1, 3)); 
if (ff>12) { ff = ff-12; 
  return ff.toString()+time.substring(3, 6)+'PM';
} else if (ff<12 && ff>0) {ff = ff;
  return time.substring(1, 6)+'AM';
} else if (ff===12) {
  return "12"+time.substring(3, 6)+'PM';
} else if (ff===24||ff===0) {
  return "12"+time.substring(3, 6)+'AM';
} else {
  return time.substring(1, 6)+'AM';
}
}

// get date in string
const getParsedDateString = (month_int, day_int, year_int) => {
year_int = parseInt(year_int); month_int = parseInt(month_int)-1;day_int = parseInt(day_int);
const full_month = get_full_month[month_int];
const parsedDateToString = `${full_month} ${day_int.toString()}, ${year_int.toString()}`;
return parsedDateToString;
} 

// get short date
const getDt = (d1o) =>{
      const time_string = d1o.dt_txt.substring(d1o.dt_txt.length-9,d1o.dt_txt.length);
      const date_string = d1o.dt_txt.substring(0,10);const day_string = date_string.substring(8,10);
      const month_string = date_string.substring(5,7);const year_string = date_string.substring(0,4);
      const date_txt = getParsedDateString(month_string, day_string, year_string);//console.log("parsed_date_txt: "+date_txt) 
      const day_dt = new Date(d1o.dt); //console.log("date_from_dt: "+day_dt);
      const day_txt = new Date(Date.parse(date_txt)); //console.log("date_from_txt: "+day_txt);
      const dateFromDT = `${daysOfWeek[day_dt.getDay()]}, ${month[day_dt.getMonth()]} ${day_dt.getDate()}`; //console.log("short_date_from_dt: "+dateFromDT);
      const dateFromTXT = `${daysOfWeek[day_txt.getDay()]}, ${month[day_txt.getMonth()]} ${day_txt.getDate()}`; //console.log("short_date_from_txt: "+dateFromTXT);
      const date = dateFromTXT; //console.log("actual_short_Date: "+date);
      return dateFromTXT;
}

// get time
const getTm = (d1o) => {
      const time_string = d1o.dt_txt.substring(d1o.dt_txt.length-9,d1o.dt_txt.length);
      const tt = format_time(time_string);
      return tt;
}

const handleHide = () => {
const search_span = document.getElementsByClassName('search-span')[0];
if (search_span.style.display==='none'){
search_span.style.display='block';
} else {
search_span.style.display='none';
}
}



</script>

<script>
const _cities = new Array("LOS ANGELES", "BEIJING", "RIO DE JANEIRO");
var last_col1=_cities[2];var last_col2=_cities[1]; var last_col3=_cities[0];
var col1_actv=true;var col2_actv=false; var col3_act=false;

const load3 = () => {
    document.getElementsByClassName('app-col')[2].innerHTML=_cities[0];
  }
load3();

const load2 = () => {
    document.getElementsByClassName('app-col')[1].innerHTML=_cities[1];
  }
load2();

const load1 = () => {
    document.getElementsByClassName('app-col')[0].innerHTML=_cities[2];
    fetchData(_cities[2]); last_col1=_cities[2];
    col1_actv=true;col2_actv=false;col3_act=false;
  }
load1();

const handle_col1 = () => {
  fetchData(last_col1);
  document.getElementsByClassName('app-col')[0].innerHTML=last_col1.toUpperCase();;
  last_col1=last_col1;col1_actv=true;col2_actv=false;col3_act=false;
  change_pointer();handleHide();
}

const handle_col2 = () => {
  fetchData(last_col2);
  document.getElementsByClassName('app-col')[1].innerHTML=last_col2.toUpperCase();;
  last_col2=last_col2;col2_actv=true;col1_actv=false;col3_act=false;
  change_pointer();handleHide();
}

const handle_col3 = () => {
  fetchData(last_col3);
  document.getElementsByClassName('app-col')[2].innerHTML=last_col3.toUpperCase();;
  last_col3=last_col3;col3_actv=true;col1_actv=false;col2_act=false;
  change_pointer();handleHide();
}

 // handle search 
  handleSearch = () => {
  search = document.getElementById('search_value').value;
  console.log(search);
  console.log("isITOkay?: "+fetchData(search));
  if(search!=="")
  document.getElementsByClassName('app-col')[0].innerText=search.toUpperCase();
  document.getElementById('search_value').value="";
  col1_actv=true;col2_actv=false;col3_act=false;last_col1=search;
  change_pointer();handleHide();}

const change_pointer = () => {
  if(col1_actv){
    document.getElementsByClassName('app-col')[0].style.borderBottom = "5px solid firebrick";
    document.getElementsByClassName('app-col')[0].style.color = "firebrick";
    document.getElementsByClassName('app-col')[1].style.borderBottom = "none";
    document.getElementsByClassName('app-col')[1].style.color = "gray";
    document.getElementsByClassName('app-col')[2].style.borderBottom = "none";
    document.getElementsByClassName('app-col')[2].style.color = "gray";
    if (document.getElementsByClassName('app-col')[0].innerText==="")load1();
  }
  else if(col2_actv){
    document.getElementsByClassName('app-col')[1].style.borderBottom = "5px solid firebrick";
    document.getElementsByClassName('app-col')[1].style.color = "firebrick";
    document.getElementsByClassName('app-col')[0].style.borderBottom = "none";
    document.getElementsByClassName('app-col')[0].style.color = "gray";
    document.getElementsByClassName('app-col')[2].style.borderBottom = "none";
    document.getElementsByClassName('app-col')[2].style.color = "gray";
    if (document.getElementsByClassName('app-col')[1].innerText==="")load2();
  } 
  else if(col3_actv){
    document.getElementsByClassName('app-col')[2].style.borderBottom = "5px solid firebrick";
    document.getElementsByClassName('app-col')[2].style.color = "firebrick";
    document.getElementsByClassName('app-col')[1].style.borderBottom = "none";
    document.getElementsByClassName('app-col')[1].style.color = "gray";
    document.getElementsByClassName('app-col')[0].style.borderBottom = "none";
    document.getElementsByClassName('app-col')[0].style.color = "gray";
    if (document.getElementsByClassName('app-col')[2].innerText==="")load3();  
  } else {
    document.getElementsByClassName('app-col')[0].style.borderBottom = "5px solid firebrick";
    document.getElementsByClassName('app-col')[0].style.color = "firebrick";
    document.getElementsByClassName('app-col')[1].style.borderBottom = "none";
    document.getElementsByClassName('app-col')[1].style.color = "gray";
    document.getElementsByClassName('app-col')[2].style.borderBottom = "none";
    document.getElementsByClassName('app-col')[2].style.color = "gray";
    handle_col1();
   }
}

</script>


</body>
</html>
