<template>
  <div id="app">
    <b-container class="text-center">
      <router-view/>
    </b-container>
    <footer>
      Made with <b-icon-heart-fill variant="danger"></b-icon-heart-fill> in VUE
    </footer>
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
}

footer{
  padding-top: 50px;
  font-weight: bolder;
  font-style: italic;
  text-align: center;
}
 
</style>


