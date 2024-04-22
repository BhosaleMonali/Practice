<template>
    <div>
        <Header/>
        <h1>Hello  {{name}}, Welcome on Home Page!!!</h1>
        <table class="restaurant-table">
            <thead>
                <tr>
                    <th>Id</th>
                    <th>Restaurant Name</th>
                    <th>Address</th>
                    <th>Actions</th>
                    <th>Delete</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="item in restaurants" :key="item.id">
                    <td>{{item.id}}</td>
                    <td>{{item.rname}}</td>
                    <td>{{item.address}}</td>
                    <td><router-link :to="'/update/'+item.id">Update</router-link></td>
                    <td><button v-on:click="deleteRestaurant(item.id)">Delete</button></td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import Header from './Header.vue'
import axios from 'axios'

export default {
    name: "HomePage",
    data() {
        return {
            name: '',
            restaurants: []
        }
    },
    components: {
        Header
    },
    methods:{
       async deleteRestaurant(id){
            // console.warn(id);
            let result = await axios.delete("http://localhost:3000/restaurant/"+id);
            if(result.status==200){
                alert("data deleted!!");
                this.load();
            }
            
        },

        async load() {
        let userInfo = localStorage.getItem('user-Info');
        this.name = JSON.parse(userInfo).name
        console.log("userInfo", userInfo);
        if (!userInfo) {
            this.$router.push({ name: 'SignUp' });
        }
        let result = await axios.get("http://localhost:3000/restaurant")
        console.log(result);
        this.restaurants = result.data;
    }
    },
    async mounted() {
        this.load();
    }
}
</script>

<style>
.nav {
    background-color: #333;
    overflow: hidden;
}

.nav a {
    float: left;
    color: #f2f2f2;
    text-align: center;
    padding: 16px 14px;
    text-decoration: none;
    font-size: 16px;
}

.nav a:hover {
    background-color: #ddd;
    color: #222;
}

.restaurant-table {
    width: 100%;
    border-collapse: collapse;
}

.restaurant-table th, .restaurant-table td {
    border: 1px solid #ddd;
    padding: 8px;
    text-align: left;
}

.restaurant-table th {
    background-color: #f2f2f2;
    color: #333;
}
</style>
