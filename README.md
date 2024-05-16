<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Weather or not</title>
    <script>var apiResponse = null;
async function run(){
     var input = document.getElementById("serchbar").value;
     var firs = input.split(' ')[0];
     var seco = input.split(' ')[1];


     console.log(firs);
     console.log(seco);
     cof = await (getData(firs, seco));
     apiResponse = JSON.stringify(cof);
     var api_response_obj = JSON.parse(apiResponse);
     console.log(api_response_obj.current.temp_c);
     var temp_c = ("The tempurature in " + firs.replace("," , "") + " is " + Math.round(api_response_obj.current.temp_c) + " Degrees Celcius");
     var temp_f = ("The tempurature in " + firs.replace("," , "") + " is " + Math.round(api_response_obj.current.temp_f) + " Degrees Fareignhight");
     var condition = ("It is " + api_response_obj.current.condition.text + " right now");
     var tomorow = ("Tomorow it will be" )
     document.getElementById("temp_c").innerHTML = temp_c;
     document.getElementById("temp_f").innerHTML = temp_f;
     document.getElementById("temp_condition").innerHTML = condition;
     
}

async function  getData( firs,  seco)

{
    var URL = `https://api.weatherapi.com/v1/current.json?q=${firs}%2C%20${seco}&key=91c2039590b440a28b8203430240503`;
    
    
    
    const response = await fetch(URL);
    const data = await response.json();
    return data;
    
    

}</script>
<styles>body {
    background-color: rgb(30, 172, 219);
}
#cool {
    border: 1px solid;
    width: 1520px;
    height: 100px;
    background-color: rgb(0, 101, 168);
    position: absolute;
    top: 0;
    z-index: 20;
}
.center {
    position: absolute;
    top: 5px;
    left: 30px;
    z-index: 30;
}
.serchbar {
    position: absolute;
    top: 40px;
    left: 1230px;
    z-index: 70;
}
.buton{
    position: absolute;
    top: 40px;
    left:  1170px;
    z-index: 80;
}
.coolyo{
    position: absolute;
    top: 200px;
    left: 425px;
    z-index: 180;
    font: Tahoma
}
.coolyof{
    position: absolute;
    top: 300px;
    left: 400px;
    z-index: 190;
    font: Tahoma
}
#main{
    position: absolute;
    top: 170px;
    left: 20px;
    border: 1px solid;
    background-color: rgb(0, 101, 168);
    width: 1500px;
    height: 500px;
}
.coolyocon{
    position: absolute;
    top: 400px;
    left: 600px;
    z-index: 190;
    font: Tahoma
}</styles>
  </head>
  <body>
    <div id="cool"></div>
    <img src="./weatherornot-high-resolution-logo.jpeg" alt="Weather or Not logo" width="200" height="200" class="center">
    <input type="text" placeholder="City, State/Province" id="serchbar" class="serchbar">
    <p id=wether></p>
    <button class="buton" id="buton" onclick="run()">Search</button>
    <h1 class="coolyo" id="coolyo">
      <span id="temp_c"></span>
    </h1>
    <h1 class="coolyocon" id="coolyocon">
      <span id="temp_condition"></span>
    </h1>
    <h1 class="coolyof" id="coolyof">
      <span id="temp_f"></span>
    </h1>
    <div id="main"></div>
  </body>
</html>
