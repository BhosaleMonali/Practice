<template>
<input type="text" placeholder="enter email" v-model="email">
<br>
<input type="text" placeholder="enter password" v-model="password">
<br>

<button v-on:click="getData()">submit</button>



</template>
<script>
export default {
    name: "BindingPage",
    data() {
        return {
            email:'null',
            password:'null',
        }
    },
    methods:{
        getData(){
            console.warn(this.email,this.password);
        },
    }
}
</script>