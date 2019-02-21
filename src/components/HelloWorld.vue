<template>
  <div id="hello-world">
    <h1>Hello {{ name }}!</h1>
    <label>Name: </label><input v-model="name">
  </div>
</template>

<script>

export default {
  data (){
    return {
      name: "Leslie",
    }
  }
}
</script>

<style scoped>
#hello-world {
  background: #fdfdfd;
  color: #333;
  margin: 0 auto;
  width: 800px;
  padding: 10px;
  /*min-height: 500px; */
}

label {
  font-weight: bold;
}
</style>
