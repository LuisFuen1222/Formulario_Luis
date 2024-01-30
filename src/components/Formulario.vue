<template>
    <div>
      <br> <br>
        <img src="../assets/LogoUT.png" />
        <div class="card custom-card">
        <h1>Formulario estudiante <p>&#128512; &#x1F393;</p> </h1>
      <form @submit.prevent="validarFormulario">
        <div>
          <label>Nombre:</label>
          <input type="text" v-model="nombre" :class="{ 'campo-invalido': errores.nombre }">
          <p v-if="errores.nombre" class="mensaje-error">{{ errores.nombre }}</p>
        </div>
        <br> <br>
        <div>
          <label>Apellido:</label>
          <input type="text" v-model="apellido" :class="{ 'campo-invalido': errores.apellido }">
          <p v-if="errores.apellido" class="mensaje-error">{{ errores.apellido }}</p>
        </div>
        <br> <br>
        <div>
          <label>Edad:</label>
          <input type="number" v-model="edad" min="0" max="60" :class="{ 'campo-invalido': errores.edad }">
          <p v-if="errores.edad" class="mensaje-error">{{ errores.edad }}</p>
        </div>
        <br> <br>
        <div>
          <label>Teléfono:</label>
          <input type="tel" v-model="telefono" :class="{ 'campo-invalido': errores.telefono }">
          <p v-if="errores.telefono" class="mensaje-error">{{ errores.telefono }}</p>
        </div>
        <br> <br>
        <div>
          <label>Género:</label>
          <select v-model="genero" :class="{ 'campo-invalido': errores.genero }">
            <option value="">Seleccione su género</option>
            <option value="masculino">Masculino</option>
            <option value="femenino">Femenino</option>
            <option value="indistinto">Indistinto</option>
          </select>
          <p v-if="errores.genero" class="error-mensaje">{{ errores.genero }}</p>
        </div>
        <br> <br>
        <button type="submit" class="btn btn-primary btn-lg btn-block">Enviar mis datos</button>
        <br> <br>
      </form>
    </div>
    <br> <br>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        nombre: '',
        apellido: '',
        edad: '',
        genero: '',
        telefono: '',
        errores: {}
      }
    },
    methods: {
      validarFormulario() {
        this.errores = {};
        let esValido = true;
        let palabrasApellido = this.apellido.toLowerCase().split(' ');
        let nombres = this.nombre.toLowerCase().split(' ');
  
        if (!this.nombre || this.nombre.length > 18) {
          this.errores.nombre = 'El nombre no puede tener más de 18 caracteres';
          esValido = false;
        }
        
        for (let nombre of nombres) {
         if (palabrasApellido.includes(nombre)) {
         this.errores.apellido = 'El apellido no puede repetirse en el campo nombres';
         esValido = false;
         break;
         }
        } 

        if (!this.telefono || this.telefono.length > 10) {
          this.errores.telefono = 'El número de teléfono no puede tener más de 10 dígitos';
          esValido = false;
        }
  
        if (!this.apellido || this.apellido.length > 18) {
          this.errores.apellido = 'El apellido no puede tener más de 18 caracteres';
          esValido = false;
        }
  
        if (this.nombre === this.apellido) {
          this.errores.nombre = 'El nombre y apellido no pueden ser iguales';
          this.errores.apellido = 'El nombre y apellido no pueden ser iguales';
          esValido = false;
        }
  
        if (!this.edad || this.edad < 0 || this.edad > 60) {
          this.errores.edad = 'Selecciona tu edad, debe estar entre 0 y 60';
          esValido = false;
        }
  
        if (!this.genero) {
          this.errores.genero = 'Selecciona un genero';
          esValido = false;
        }

        return esValido;
      }
    }
  }
  </script>
  
  <style scoped>
  .campo-invalido {
    border-color: red;
  }
  
  .error-mensaje {
    color: red;
  }
  .custom-card {
  background-color: #ccebaf;
  line-height: 1.1;
  border: solid #9ac37f
}

  </style>