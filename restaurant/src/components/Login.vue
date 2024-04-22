<template>

<div class="login-container">
    <h1>Login</h1>
    
    <input type="text" v-model="email" placeholder="Enter email"><br/><br/>
    <input type="password" v-model="password" placeholder="Enter password"><br/><br/>
    <button v-on:click="login">Login</button><br/>
    <router-link to="/">Sign Up</router-link>
</div>
</template>

<script>
import axios from 'axios'
export default {
    name:"LoginPage",
    data(){
        return {
            email:'',
            password:''
        }
    },
    methods:
    {
        async login(){
            let result = await axios.get(`http://localhost:3000/user?email=${this.email}&password=${this.password}`);
            console.log("result login",result);
            if (result.status == 200 && result.data.length>0) {
                localStorage.setItem("user-Info", JSON.stringify(result.data[0]));
                this.$router.push({
                    name: 'Home'
                })
            }
        }
    },
    mounted(){
        let userInfo = localStorage.getItem('user-Info');
        console.log("userInfo", userInfo);
        if(userInfo) {
            this.$router.push({ name:'Home' });
        }
    }
}
</script>

<style>
.login-container {
    max-width: 400px;
    margin: auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f9f9f9;
}

h1 {
    text-align: center;
}

input[type="text"],
input[type="password"] {
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
}

button {
    width: 100%;
    padding: 10px;
    margin-top: 10px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #0056b3;
}

router-link {
    display: block;
    text-align: center;
    margin-top: 10px;
    text-decoration: none;
    color: #007bff;
}

router-link:hover {
    color: #0056b3;
}
</style>
