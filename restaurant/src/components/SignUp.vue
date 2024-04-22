<template>
    <div class="signup-container">
        <img src="https://th.bing.com/th/id/OIP.Nri54AXD85UhWssljHo65gHaIq?w=131&h=180&c=7&r=0&o=5&dpr=1.5&pid=1.7" alt="Logo" class="logo">
        <h1>Sign Up</h1>
        <div>
            <input type="text" v-model="name" placeholder="Enter name"><br/><br/>
            <input type="text" v-model="email" placeholder="Enter email"><br/><br/>
            <input type="password" v-model="password" placeholder="Enter password"><br/><br/>
            <button v-on:click="signUp">Sign Up</button><br/>
            <router-link to="/login">Login</router-link>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    name: "SignUp",
    data() {
        return {
            name: '',
            email: '',
            password: ''
        }
    },
    methods: {
        async signUp() {
            console.warn("signUp");
            const result = await axios.post("http://localhost:3000/user", {
                "name": this.name,
                "email": this.email,
                "password": this.password
            });
            console.warn("result", result);
            if (result.status == 201) {
                localStorage.setItem("user-Info", JSON.stringify(result.data));
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
.signup-container {
    max-width: 400px;
    margin: auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f9f9f9;
}

.logo {
    display: block;
    margin: auto;
    margin-bottom: 20px;
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
