<template>
  <img alt="Vue logo" src="./assets/logo.png">

  <HelloWorld/>
 
      
     <LoginForm/>

  
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
// import Home from './components/Home.vue'
// import Binding from './components/Binding.vue'
// import parent from './components/Parent.vue'
// import Homeparent from './components/HomeParent.vue'
import LoginForm from './components/LoginForm.vue'

export default {
  name: 'App',
  components: {
    
    //  parent,
    HelloWorld,
    // Binding,
    // Homeparent,
    LoginForm,
    
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
