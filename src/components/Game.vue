<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>{{ rules }}</h2>

    <ul>
      <li>{{rockwins}}</li>
      <li>{{paperwins}}</li>
      <li>{{scissorwins}}</li>
    </ul>

  </div>
</template>

<script>
export default {
  name: 'Game',
  props: {
    msg: String,
    rules: String,
    paperwins: String,
    rockwins: String,
    scissorwins: String
  }
}
</script>


<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.hello{
  text-align: center;
}
</style>
