<template>
  <div id="app">
    <Game msg="Player vs Computer: Rock Paper Scissors"
    rules="The rules are simple:"
    paperwins="Papers Beats Rock"
    rockwins="Rock Beats Scissors"
    scissorwins="Scissors Beats Paper"/>

    <login :username="usernames"
    :loggedin="loggedin"/>

    <Options :opponentschoice="opponentschoice"
    :loggedin="loggedin"/>

    <Results win="Wins"
    loss="Losses"
    draw="Draws"
    totalgames="Total Games"
    :wins="wins"
    :losses="losses"
    :draws="draws"
    :totgames="total"
    :loggedin="loggedin"/>



  </div>
</template>

<script>
import Game from './components/Game.vue'
import Options from "@/components/Options";
import Results from "@/components/Results";
import users from "./assets/users.json";
import Login from "@/components/login";
export default {

  name: 'App',
  data(){
  return{
    wins:0,
    losses:0,
    draws:0,
    total:0,
    opponentschoice:"",
    usernames:"try",
    passwords:"again",
    users:users,
    loggedin:false,
    position:0

    }
  },components: {
    Login,
    Options,
    Game,
    Results
  },methods: {
    rps:function(item) {
      if(this.wins==10||this.losses==10){
        this.wins=0;
        this.losses=0;
        this.draws=0;
        this.total=this.draws+this.losses+this.wins;
      }
      const choices=["Rock","Paper", "Scissors"];
      var playerResult=choices[item];
      var result=Math.floor(Math.random()*3);
      var computerResult=choices[result];

      if(playerResult=="Rock"){
        if(computerResult=="Scissors"){
          this.incrementwins();
        }else if(computerResult=="Paper") {
          this.incrementloss();
        }else{
          this.incrementdraw();
        }
      }else if(playerResult=="Paper"){
        if(computerResult=="Rock"){
          this.incrementwins();
        }else if(computerResult=="Scissors") {
          this.incrementloss();
        }else{
          this.incrementdraw();
        }
      }else if(playerResult=="Scissors") {
        if (computerResult == "Paper") {
          this.incrementwins();
        } else if (computerResult == "Rock") {
          this.incrementloss();
        } else {
          this.incrementdraw();
        }
      }
      this.incrementtotal();
    },incrementwins(){
      this.wins++;
      if(this.wins==10){
        alert("you win!");
      }
    },incrementloss(){
      this.losses++;
      if(this.losses==10){
        alert("you lose!");
      }
    },incrementdraw(){
      this.draws++;
    },incrementtotal(){
      this.total=this.draws+this.wins+this.losses;
    },login(username, password){
      var items=this.users.users.length;
      for (var i=0;i<items;i++){

          if(this.users.users[i].username==username &&this.users.users[i].password==password) {
            this.usernames = username;
            this.passwords = password;
            this.position=i;

            this.wins=this.users.users[i].wins;
            this.losses=this.users.users[i].loss;
            this.draws=this.users.users[i].draw;
            this.total=this.draws+this.losses+this.wins;
            this.loggedin=true;
          }
      }


    },loggedout(logcheck,name,password){
      this.users.users[this.position].wins=this.wins;
      this.users.users[this.position].loss=this.losses;
      this.users.users[this.position].draw=this.draws;
      this.losses=0;
      this.wins=0;
      this.draws=0;
      this.total=0;
      this.usernames=name;
      this.passwords=password;
      this.loggedin=logcheck;
    },register(uname,password){
      if(uname!="" && password!="") {
        var item=false;
        var items=this.users.users.length;
        for (var i=0;i<items;i++){

          if(this.users.users[i].username==uname &&this.users.users[i].password==password) {
            item=true;
            break;
          }
        }
        if(!item) {
          this.users.users.push({username: uname, password: password,wins:0,loss:0,draw:0});
          alert("Registration successful");
          this.usernames=uname;
          this.passwords=password;
          this.position=items;




          this.loggedin=true;
        }else{
          alert("user already exists");
        }
      }else{
        alert("no information detected");
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  font-size:calc(12px + .8vw);
}
h2{
  font-size:calc(8px + .6vw);
}

@media screen and (max-width:575px){
  h1{font-min-size: 12px;}
  h2{font-min-size: 8px;}
}
@media screen and (min-width:1600px){
  h1{font-min-size: 26px;}
  h2{font-min-size: 18px;}
}

@media screen and (max-width:575px){
  h1{font-min-size: 12px;}
  h2{font-min-size: 8px;}
}
</style>
