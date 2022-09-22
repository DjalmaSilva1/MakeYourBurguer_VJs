<template>
  <NavBar :logo="logo_src" :alt="app_name"/>
  <router-view/>
  <Footer/>
</template>

<script>
import NavBar from './components/NavBar.vue';
import Footer from './components/Footer.vue';
  export default {
    name: "App",
    components:{
    NavBar,
    Footer
},
  data(){
    return{
      logo_src: "..//public/img/LogoBranco.jpg",
      app_name: "make your Burguer",
    }
  }
  }
</script>

<style>
  * {
    font-family: Arial, Helvetica, sans-serif;
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }
  .main-container{
    margin: 50px;
    min-height: 250px;
  }
  h1{
    text-align: center;
    margin-bottom: 30px;
    font-size: 42pxc;
    color: #000;
  }
</style>
