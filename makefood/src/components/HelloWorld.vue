<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      For a guide and recipes on how to configure / customize your kitchen skills!
    </p>
  </div>
</template>

<script>
export default {
  name: 'makefood',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  color: #000;
  font-size: 42px;
  font-weight: 700;
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
p {
  font-size: 18px;
  color: #333;
}
</style>
