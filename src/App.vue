<template>
  <div id="app">
    <fullscreen ref="fullscreen">
    <link rel="stylesheet" href="https://pro.fontawesome.com/releases/v5.10.0/css/all.css" integrity="sha384-AYmEC3Yw5cVb3ZcuHtOA93w35dYTsvhLPVnYs9eStHfGJvOvKxVfELGroGkvsg+p" crossorigin="anonymous"/>
    <b-container class="text-center">
      <router-view/>
    </b-container>
    <footer>
      Made with <b-icon-heart-fill variant="danger"></b-icon-heart-fill> in <i class="fab fa-vuejs"></i> Vue
    </footer>
    </fullscreen>
  </div>
</template>

<style>

body{
  height: 100%;
  width: 100%;
  background-image: url('./assets/bg.jpg');
  background-size: cover;
  background-repeat: no-repeat;
}

#app{
  color: white;
  height: 100%;
  width: 100%;
}

footer{
  padding-top: 140px;
  font-weight: bolder;
  font-style: italic;
  text-align: center;
  padding-bottom: 30px;
}
 
</style>


