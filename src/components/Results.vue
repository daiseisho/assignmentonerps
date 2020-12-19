<template>
<div v-show="loggedin" id="res">
  <table >
    <tr>
      <th>{{win}}</th>
      <th>{{loss}}</th>
      <th>{{draw}}</th>
      <th>{{totalgames}}</th>
    </tr>
    <tr>
      <td id="wins">{{wins}}</td>
      <td id="losses">{{losses}}</td>
      <td id="draws">{{draws}}</td>
      <td id="total">{{totgames}}</td>
    </tr>
  </table>
</div>
</template>

<script>
export default {
  name: "Results",
  props: {
    loggedin:Boolean,
    win: String,
    loss: String,
    draw: String,
    totalgames: String,
    totgames: String,
    wins: Number,
    losses: Number,
    draws: Number
  }
}
</script>

<style scoped>
#res{
  width:49.8%;
  display: inline-table;
  text-align: center;
}
@media screen and (max-width:575px){

  #res{
    width:100%;
    display: inline-table;
    text-align: center;
  }
}
</style>