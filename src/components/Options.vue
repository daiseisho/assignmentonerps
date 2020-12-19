<template>
  <div v-show="loggedin" id="buttons">
    <table>
      <tr>
        <td></td>
      </tr>
      <tr>
        <td>
            <img id="rock" src="../assets/rockunselected.png" alt="Rock unchosen" @click="resrock()">
        </td>
        <td>
          <img id="paper" src="../assets/paperunselected.png" alt="paper unchosen" @click="respaper()">
        </td>
        <td>
          <img id="scissors" src="../assets/scissorsunselected.png" alt="scissors unchosen" @click="resscissor()">
        </td>

      </tr>
    </table>
  </div>
</template>

<script>

export default {
name: "Options",methods: {
   resrock() {
      var res = 0;
      this.$parent.rps(res);
    },
    respaper() {
      var res = 1;
      this.$parent.rps(res);
    },
    resscissor() {
      var res = 2;
      this.$parent.rps(res);
    }, props: {
      opponentschoice: String
    }
  },props:{
  loggedin:Boolean
  }
}
</script>

<style scoped>
#rock:hover{
  content:url("../assets/rock.png")
}
#paper:hover{
  content:url("../assets/paper.png")
}
#scissors:hover{
  content:url("../assets/scissors.png")
}
img{
  max-width: 100%;

}
#buttons{
  width:49.8%;
  display: inline-table;
  text-align: center;
}
@media screen and (max-width:575px){
  img{
    min-width: 75px;
  }
  #buttons{
    width:100%;
    display: inline-table;
    text-align: center;
  }
}
@media screen and (min-width:1600px){

}
</style>