<template>
  <v-app>
    <v-app-bar
      app
      color="white"      
    >
    <v-img src='./assets/logopadrao.png' style="max-width:200px;" />   
    
    Consulta de aceitações - Lei Geral de Proteção aos Dados
    </v-app-bar>

    <v-main class="body">
      
      <router-view>
      
      </router-view>
    </v-main>

    
  </v-app>
</template>

<script>


export default {
  name: 'App',

  components: {
    //
  }

 
}
</script>

<style scoped>
.body {
  background-image: url('./assets/searchlogo.svg');
}
</style>