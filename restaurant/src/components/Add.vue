<template>
    <Header/>
    <h1>Hello, Welcome to Add Restaurant Page!!!</h1>
    <form class="add-form">
        <input type="text" placeholder="Enter Restaurant name" v-model="restaurant.rname"><br/><br/>
        <input type="text" placeholder="Enter Restaurant Address" v-model="restaurant.address"><br/><br/>
        <button type="button" v-on:click="addRestaurant">Add Restaurant</button>
    </form>
</template>

<script>
import Header from './Header.vue'
import axios from 'axios'
export default {
    name: "AddPage",
    data() {
        return {
            restaurant: {
                rname: '',
                address: ''
            }
        }
    },
    components: {
        Header
    },
    methods: {
        async addRestaurant() {
            let result = await axios.post("http://localhost:3000/restaurant", {
                "rname": this.restaurant.rname,
                "address": this.restaurant.address
            });

            console.log("Restaurant result after post", result);
            if (result.status == 201) {
                this.$router.push({
                    name: 'Home'
                });
            }
        }
    }
}
</script>

<style>
/* Header styles */
.Header {
    background-color: #333;
    overflow: hidden;
}

.Header a {
    float: left;
    color: #f2f2f2;
    text-align: center;
    padding: 16px 14px;
    text-decoration: none;
    font-size: 16px;
}

.Header a:hover {
    background-color: #ddd;
    color: #222;
}

/* Form styles */
.add-form {
    max-width: 400px;
    margin: auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f9f9f9;
}

.add-form input[type="text"] {
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
}

.add-form button {
    width: 100%;
    padding: 10px;
    margin-top: 10px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

.add-form button:hover {
    background-color: #0056b3;
}
</style>
