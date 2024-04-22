<template>
<h1>
    send data child to parent in vuejs3</h1>
<UserChild :getUserName="getUserName"/>
</template>

<script>
import UserChild from './UserChild.vue'
export default {
    name: 'HomeParent',
    components: {
        UserChild
    },
    methods: {
        getUserName(name) {
            alert(name);
        }
    }
}
</script>
