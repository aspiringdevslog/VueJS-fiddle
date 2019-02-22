<template>
  <div>
    <hello-world></hello-world>
    <team-composition></team-composition>
    <optimize-monster></optimize-monster>
  </div>
</template>

<script>

import HelloWorld from './components/HelloWorld.vue'
import TeamComposition from './components/TeamComposition.vue'
import OptimizeMonsterRune from './components/OptimizeMonsterRune.vue'

export default {
  components: {
    'hello-world': HelloWorld,
    'team-composition': TeamComposition,
    'optimize-monster': OptimizeMonsterRune

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
