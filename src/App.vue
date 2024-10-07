<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Generation from './components/Generation.vue'
import Header from './components/Header.vue'
import Hello from './components/Hello.vue'
</script> 

<script>
export default {
  data() {
    return {
      isGenerationHidden: true,
      generationStyle: { opacity: '1' },
    }
  },
    methods: {
      receiveData(value) {
        this.isGenerationHidden = value;
        setTimeout(() => {
            this.generationStyle = { opacity: '1' };
          }, 50);
        
      }
    }
}
</script>

<template>
<!--   <Header/> -->
  <div class="wrapper">
<!--     <Hello @send-data="receiveData"/> -->
    <Generation v-if="isGenerationHidden" :style='generationStyle'/>
  </div>
</template>

<style scoped>
</style>
