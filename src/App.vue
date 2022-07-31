<template>
  <div id="app" class="app">
  <div class="header">
    <h1>Banco Mision Tic</h1>
    <nav>
      <button v-if="is_auth">Inicio</button>
      <button v-if="is_auth">Cuenta</button> 
      <button v-if="is_auth">Cerrar Sesion</button>
      <button v-if="!is_auth" v-on:click="loadLogIbn">Iniciar Sesion</button>
      <button v-if="!is_auth" v-on:click="loadSignUp">Registrarse</button>
    </nav>
  </div>

  <div class="main-component">
    <router-view
      v-on:completedLogIn="completedLogIn"
      v-on:completedSignUp="completedSignUp">
      </router-view>
  </div>

  <div class="footer">
    <h2> Mision TIC 2022</h2>
  </div>

  </div>
</template>
<script>
import { functionTypeAnnotation } from '@babel/types'

export default {
  name:'App',

  data: function(){

  },
  methods: {
      verifyAuth: function(){
        if (this.is_auth == false) {
          this.$router.push({name: "logIn"})
        }
      },

      loadLogin: function () {
        this.$router.push({name: "logIn"})
      },

      loadSignUp: function(){
        this.$router.push({name: "signUop"})
      },

      completedLogIn: function(data) {},

      completedSignUp: function(data) {},

  },
  created: function(){
     this.verifyAuth()
  }
}
</script>

<style >
  body{
    margin: 0 0 0 0;
  }

  .header{
    margin: 0;
    padding: 0;
    width: 100%;
    height: 10vh;
    min-height: 100px;

    background-color: #283747;
    color: #e5e7e9;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .header h1{
    width: 20%;
    text-align: center;
  } 
</style>
