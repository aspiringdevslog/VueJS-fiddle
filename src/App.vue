<template>
  <div>
    <hello-world></hello-world>
    <team-composition></team-composition>
  </div>
</template>

<script>

import HelloWorld from './components/HelloWorld.vue'
import TeamComposition from './components/TeamComposition.vue'

export default {
  components: {
    'hello-world': HelloWorld,
    'team-composition': TeamComposition

  },
  data: function(){
    return{

    }
  }
}
</script>

<style scoped>
body {
  font: Arial; 
}

</style>
