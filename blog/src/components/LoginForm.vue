<template>
<h1>
    Login</h1>
<p>{{form}}</p>
<form>

    <label>Email:</label>
    <input type="text" placeholder="enter Email" v-model="form.email">
    <br><br/>

    <label>Password:</label>
    <input type="password" placeholder="enter Password" v-model="form.password">
    <br><br/>
    <label>Country:</label>
    <select v-model="form.country">
    <option>India</option>
    <option>USA</option>
    <option>Japan</option>
    </select>
    <br><br/>
    <label>Technology:</label>
    <label>java</label>
    <input type="checkbox" value="java" v-model="form.technology">

    <label>dotnet</label>
    <input type="checkbox" value="dotnet" v-model="form.technology">
    <br><br/>

    <label>Gender:</label>
    <label>Male</label>
    <input type="radio" value="Male" name="gender" v-model="form.gender">

    <label>Female</label>
    <input type="radio" value="Female" name="gender" v-model="form.gender">
    <br><br/>
    <button v-on:click="login" type="button">Submit</button>
</form>
<div v-if="error.length > 0">
    <h2>Error:</h2>
    <ul>
        <li v-for="err in error" :key="err">{{ err }}</li>
    </ul>
</div>
</template>

<script>
export default {
    name: "LoginForm",
    data() {
        return {
            form: {
                email: '',
                password: '',
                country: '',
                technology: [],
                gender: ''
            },
            error: [],
        }
    },
    methods: {
        // login() {
        //     // for(const item in this.form )
        //     // {
        //     //     if(this.form[item]==="" || this.form[item].length===0)
        //     //     {
        //     //         this.error.push(item);
        //     //     }
        //     // }
        //      const formDataString = `Email: ${this.form.email}\nPassword: ${this.form.password}\nCountry: ${this.form.country}\nTechnology: ${this.form.technology.join(', ')}\nGender: ${this.form.gender}`;
        //      alert("Login data:",this.formDataString);
        //     //  console.log("Login data:", this.form);
        // }
        login() {
            // const formDataString = `Email: ${this.form.email}\nPassword: ${this.form.password}\nCountry: ${this.form.country}\nTechnology: ${this.form.technology.join(', ')}\nGender: ${this.form.gender}`;
            // alert("Login data:\n" + formDataString);
            // console.log("Login data"+formDataString);
            console.warn(this.form)
            for (const item in this.form) {
                if (this.form[item] === "" || this.form[item].length === 0) {
                    this.error.push(item);
                }
            }
            // alert("Login data:", this.error);
        }
    }
}
</script>
