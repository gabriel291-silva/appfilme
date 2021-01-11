<template>
<div id="app">

 

<div class="search-box">
 <input type="text" class="search-txt"  v-model="searchkey" name="" placeholder="Tipo de Busca">
 <a class="search-btn" @click="serachmovie">P</a>
</div>
<br>
<br>








<div v-for="(tst,index) in teste" :key="index">
<card :urlposter="tst.Poster" :name="tst.Title" :ano="tst.Year" :tipo="tst.Type"/>
    </div>




   
 </div>
</template>

<script>
import axios from 'axios';
import card from '../src/components/card.vue'
export default {
  name: 'App',
components:{
card
},


   data(){
return{
   searchkey:"",
 
teste: []
}

  },

methods:{
  serachmovie(){
  axios.get("http://www.omdbapi.com/?s="+this.searchkey+"&plot=full&apikey=e1b97047").then(res=>{
    console.log("pegou a lista de filme ");
    this.teste=res.data.Search;
    console.log(this.teste);
  })
  
}} 
}
</script>

<style>
body{
  background-image: url('../src/assets/artefundo4.jpg');
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

 .search-box{
    position: absolute;
    top: 10%;
    left: 50%;
   
    transform: translate(-50%,-50%);
    background: rgba(80, 5, 93, 0.589);
    height: 50px;
    border-radius: 50px;
    padding: 6px;
   }
   .search-box:hover > .search-txt{
    width: 240px;
    padding: 0 6px;
   }
   .search-box:hover > .search-btn{
    background:blueviolet;
   }
   .search-btn{
    color:white;
    float: right;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    display: flex;
    background: rgb(53, 2, 73) ;
    justify-content: center;
    align-items: center;
    text-decoration: none;
   }
   .search-txt{
    border: none;
    background: none;
   
    text-align: center;
    outline: none;
    padding: 0;
    font-size: 15px;
    color: white;
    transition: 0.3s;
    line-height: 50px;
    width: 0;
   }
</style>
