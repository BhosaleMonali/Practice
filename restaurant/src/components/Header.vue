<template>
<div class="nav">
    <router-link to="/home" href="home">Home</router-link>
    <router-link to="/add" href="home">Add</router-link>

    <a v-on:click="logout" href="#" type="button">Logout</a>
</div>
</template>

<script>
export default {
    name: "HeaderPage",
    methods: {
        logout() {
            // console.warn("logout");
            localStorage.clear();
             this.$router.push({
                    name: 'Login'
                })

        }
    }
}
</script>
