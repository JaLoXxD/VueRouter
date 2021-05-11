<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <Titulo :texto="titulo" /> 
  </div>
</template>

<script>
import Titulo from '../components/Titulo'

export default {
  name: 'Home',
  components: {
    Titulo
  },
  data() {
    return {
      titulo: 'Este es mi home en Vue.Js',
    }
  }
}
</script>
