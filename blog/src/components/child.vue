<template>
<h1>child Component</h1>
<h3>name:{{name}}</h3>
<h3>Username:{{user.name}} useremail:{{user.email}}</h3>
<button v-on:click="getData()">ClickHere</button>
</template>
<script>
export default {
    name:"childPage",
    props:{
        name:String,
        user:Object,
        getData:Function
    }
    
    

}
</script>