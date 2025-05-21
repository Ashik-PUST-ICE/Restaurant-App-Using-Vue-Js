<template>
  <div class="signup-container">
    <img class="logo" src="../assets/new.png" alt="Logo" />
    <h1>Sign Up</h1>
    <div class="form-container">
      <input type="text" v-model="name" placeholder="Enter Name" />
      <input type="email" v-model="email" placeholder="Enter Email" />
      <input type="password" v-model="password" placeholder="Enter Password" />
      <button v-on:click="signUp">Submit</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'SignUp',
  data() {
    return {
      name: '',
      email: '',
      password: ''
    };
  },
  methods: {
   async signUp() {
      console.warn("signUp",this.name,this.email,this.password);
      let result =await axios.post("http://localhost:3000/user",{
        emai:this.email,
        name:this.name,
        password:this.password
      }); 
      console.warn(result);
      if(result.status==201)
      {
        alert("Sign Up Done")
      }
      localStorage.setItem("user-info",JSON.stringify(result.data))
    }
  }
}

</script>

<style scoped>
.signup-container {
  max-width: 400px;
  margin: 80px auto;
  padding: 30px;
  border-radius: 15px;
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
  background-color: #fff;
  text-align: center;
  font-family: Arial, sans-serif;
}

.logo {
  width: 100px;
  margin-bottom: 20px;
}

h1 {
  margin-bottom: 25px;
  font-size: 28px;
  color: #333;
}

.form-container {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

input {
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 8px;
  font-size: 16px;
  outline: none;
  transition: 0.3s ease;
}

input:focus {
  border-color: #007bff;
  box-shadow: 0 0 5px rgba(0, 123, 255, 0.3);
}

button {
  padding: 12px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #0056b3;
}
</style>
