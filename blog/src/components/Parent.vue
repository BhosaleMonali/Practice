<template>
<h1>
    Pass Data to child components </h1>
<child name="Monali Bhosale" :user="user" :getData="getData" />
</template>

<script>
import child from './child.vue'
export default {
    name: "ParentPage",
    components: {
        child
    },
    data() {
        return {
            user: {
                name: "peter",
                email: "peter@gamil.com"
            }
        }
    },
    methods: {
        getData() {
            console.warn("Parent data fetch:");
        }
    }

}
</script>
