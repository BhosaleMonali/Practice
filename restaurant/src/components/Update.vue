<template>
    <Header/>
    <h1>Hello, Welcome to Update Restaurant Page!!!</h1>
    <form class="update-form">
        <input type="text" placeholder="Enter Restaurant name" v-model="restaurants.rname"><br/><br/>
        <input type="text" placeholder="Enter Restaurant Address" v-model="restaurants.address"><br/><br/>
        <button type="button" v-on:click="updateRestaurant">Update Restaurant</button>
    </form>
</template>

<script>
import Header from './Header.vue'
import axios from 'axios'
export default {
    name: "UpdatePage",
    components: {
        Header
    },
    data() {
        return {
            restaurants: {
                rname: '',
                address: ''
            }
        }
    },
    methods: {
        async updateRestaurant() {
            let result = await axios.put("http://localhost:3000/restaurant/" + this.$route.params.id, {
                "rname": this.restaurants.rname,
                "address": this.restaurants.address
            });

            console.log("Restaurant result after update", result);
            if (result.status == 200) {
                this.$router.push({
                    name: 'Home'
                })
            }
        }
    },
    async mounted() {
        console.log(this.$route.params.id);
        let result = await axios.get("http://localhost:3000/restaurant/" + this.$route.params.id);
        console.log(result);
        this.restaurants = result.data;
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
.update-form {
    max-width: 400px;
    margin: auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f9f9f9;
}

.update-form input[type="text"] {
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
}

.update-form button {
    width: 100%;
    padding: 10px;
    margin-top: 10px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

.update-form button:hover {
    background-color: #0056b3;
}
</style>
