<template>
<h1> Home Component </h1>
<h1>email {{email}}</h1>
<h3>Mobile {{mobile=90908}}</h3>
<h3>name: {{getName("Hritik")}}</h3>
<h3>data:{{getData().email}}</h3>
<button v-on:click="test()">clickme</button>
<input type="text" v-model="count1">
<h3 >{{count1}}</h3>
</template>

<script>
export default {
    name: 'HomePage',
    data() {
        return {
            email: "abc@exampl.com",
            mobile: 1234456,
            count:0,
            count1:0,
            // getname:function(){

            //     return "Monali"
            // }
        }
    },

    methods: {
        getName(name) {
            return name;
        },
        getData() {
            return {
                name: "ABC",
                email: this.email,
            }
        },
        test(){
                this.count=this.count+1;
            alert("onclick event called!"+ this.count);
        }

    }
}
</script>

<style>
h1 {
    color: blue;
}
</style>
