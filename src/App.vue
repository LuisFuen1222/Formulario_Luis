<template>
  <div id="app">
    <Formulario />
  </div>
</template>

<script>
import Formulario from './components/Formulario.vue';

export default {
  components: {
    Formulario
  }
};
</script>

<style>
/*  estilos globales */
body {
  background-color: #e5ffc7; 
  background-image: url(https://png.pngtree.com/background/20230612/original/pngtree-green-forest-with-trees-is-shown-picture-image_3177167.jpg);
  background-repeat: no-repeat;
  background-size: cover;
  background-attachment: fixed;
  backdrop-filter: blur(5px);
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  color: #2c3e50;
  line-height: 1.6;
  text-align: center;
}

#app {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
.h1{
  order: 1;
}

</style>
