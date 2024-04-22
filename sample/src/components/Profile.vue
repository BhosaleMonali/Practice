<template>
<h1>
    Profile Page:{{profile}}</h1>
</template>

<script>
import {
    useRoute
} from 'vue-router'
export default {
    name: 'ProfilePage',
    data() {
        return {
            profile: ''
        }
    },
    mounted() {
        const route = useRoute();
        console.warn("Route", route.params);
        this.profile = route.params.name;
    }
}
</script>
