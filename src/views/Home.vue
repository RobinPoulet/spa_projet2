<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <Acceuil />
    
    
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from '@/components/HelloWorld.vue'
import Acceuil from '@/components/Acceuil.vue'


export default {
  name: 'Home',
  components: {
   // HelloWorld,
    Acceuil,
    
  }
}
</script>
