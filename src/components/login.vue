<template>
  <div class="login">

    <label v-show="!loggedin"><b>Username</b></label>
    <input id="uname" v-show="!loggedin" type="text" placeholder="Enter Username">
    <br>
    <label v-show="!loggedin"><b>Password</b></label>
    <input id="passw" v-show="!loggedin" type="password" placeholder="Enter password">
    <br>
    <button v-show="!loggedin" @click="sendData">login</button>
    <button v-show="!loggedin" @click="register">Register</button>
    <label v-show="loggedin">welcome {{username}}<br></label>
    <button v-show="loggedin" @click="logout">log out</button>

  </div>
</template>

<script>
export default {
  name: 'login',
  methods:{
    sendData(){
      var uname=document.getElementById("uname").value;
      var password=document.getElementById("passw").value;
      this.$parent.login(uname,password);
    },
    logout(){
      var inspect=false;
      var uname="";
      var password="";
      this.$parent.loggedout(inspect,uname,password);
    },register(){
      var uname=document.getElementById("uname").value;
      var password=document.getElementById("passw").value;
      this.$parent.register(uname,password);
    }
  },props: {
    loggedin: Boolean,
    username: String
  }
}
</script>


<style scoped>
.login{
  text-align:center;
}
</style>
