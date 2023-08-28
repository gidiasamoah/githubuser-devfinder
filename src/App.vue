<script setup>
import TheContentComponent from './components/TheContentComponent.vue';
import TheHeaderComponent from './components/TheHeaderComponent.vue';


</script>

<template>
 
  <div class="main">
    <TheContentComponent />
  </div>
</template>

<style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100;200;300;400;500;700;800&family=Space+Mono:ital,wght@0,400;0,700;1,400;1,700&display=swap');
  *{
    font-family: Space Mono;
    background: #F6F8FF;


}
  
  .main{
    max-width: 730px;
    margin: 0 auto;
  }
</style>
