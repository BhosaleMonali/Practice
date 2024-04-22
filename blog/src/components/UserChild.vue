<template>
<h2>
    User Component</h2>
<button v-on:click="getUserName(userName)">send username</button>
</template>

<script>
export default {
    name: 'UserChild',
    data() {
        return {
            userName: "Peter"
        }
    },
    props: {
        getUserName: Function
    }
}
</script>
