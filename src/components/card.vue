<template>
    <div id="boxcard">
        <br>
<div class="card">
  <br>
  <img class="imgf" :src="urlposter" >
  <div class="container">
    <h4>nome: {{name}}</h4>
    <h4>tipo {{tipo}} </h4>
    <h4>ano: {{ano}}</h4>
    
    <button class="btncard">mais</button>
    <br>
    <br>
  </div>
</div>
<br>







    </div>
    <br>
    <br>
</template>

<script>
import axios from 'axios';

export default {
    props:{
    urlposter: String,
    name: String,
    ano:Number,
    tipo:String
},
data(){

return{

idomdapi:""

}

},
methods:{
  serachmovie(){
  axios.get("http://www.omdbapi.com/?i=tt0372784 &apikey=e1b97047").then(res=>{
    console.log("pegou a lista de filme ");
    this.teste=res.data.Search;
    console.log(this.teste);
  })
  
}}

}
</script>

<style scoped>
.card{
  background-color:  rgb(53, 2, 73);
  width: 230px;
  height: 250px;
  display: block;
margin-left: auto;
margin-right: auto;
border-radius: 10px;
}
.btncard{
  background-color: violet;
}
.container{
  color: aliceblue;
  font-family: monospace;
  font-size: 20px;

border-radius: 10px;
  background-color: rgba(59, 6, 95, 0);
}
.imgf{
 width: 200px;
  height: 220px;
  border-radius: 10px;


}
#boxcard{
background-color:  rgba(80, 5, 93, 0.589);
width: 320px;
height: 520px;
border-radius: 50px;
display: block;
margin-left: auto;
margin-right: auto;


}
.btncard{
color:aliceblue;
font-family: monospace;
font-size: 20px;
background-color:  rgb(53, 2, 73);
height: 30px;
width: 100px;
border-radius: 30px;
border: none;

}
</style>