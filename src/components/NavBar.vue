<template>
  <div id="nav">
    <router-link to="/" id="logo-url">
        <img style="
        width: 100px;
        height: 100px;" 
        
        :src="logo" :alt="alt" id="logo">
    </router-link>
    <router-link to="/">Home</router-link> 
    <router-link to="/pedidos">Pedidos</router-link>
  
  </div>
</template>

<script>
export default {
name: "NavBar",
props: ["logo", "alt"],

}
</script>

<style>
    #nav{
        background-color: #fff;
        border-bottom: 4px solid #fff;
        padding: 15px 50px;
        display: flex;
        justify-content: flex-end;
        align-items: center;
    }
    #nav #logo-url{
        margin: auto;
        margin-left: 0;
        width: 40px;
        height: 40px;
    }
    #nav a{
        color: #000;
        text-decoration: none;
        margin: 12px;
        transition: -5s;
    }
    #nav a:hover{
        color: #FCBA03;
    }
</style>