<template>
<h1>Home Page</h1>
<table class="todo-table">
<thead>
<tr>
<th> Id</th>
<th>Title</th>

</tr>
</thead>
<tbody>

<tr v-for="item in list" :key="item.id">
<td>{{item.id}}</td>
<td> {{item.completed}}</td>
</tr>
</tbody>
</table>
</template>

<script>
import axios from 'axios';
export default {

    name: 'HomePage',
    data() {
        return {
            list: []
        };
    },

    async mounted(){
        let result=await axios.get("https://jsonplaceholder.typicode.com/todos");
        console.log("api data",result.data);
        this.list=result.data;
    }

}
</script>
<style>
.todo-table {
  width: 100%;
  border-collapse: collapse;
}

.todo-table th, .todo-table td {
  border: 1px solid #ddd;
  padding: 8px;
  text-align: left;
}

.todo-table th {
  background-color: #f2f2f2;
  font-weight: bold;
}
</style>
