<template>
<div>
  <HelloWorld />
  <div class="container text-center mx-auto mt-4 mb-3">
  <router-link class="link1 mx-5" to="/">Global Data</router-link>
   <router-link class="link1" to="/about">Country Data</router-link>
  <router-view/>
  </div>
</div>
  
</template>
<script>
import  HelloWorld  from '@/components/HelloWorld.vue'
export default{
  components:{
    HelloWorld,
  }
}
</script>
<style>
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.link1{
  text-decoration: none;
  color: #2e6e89;
}
.link1:hover{
  color: #2e6e;
}
</style>


