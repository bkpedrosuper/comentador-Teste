<template>
  <div id="text">
    <p>{{comments}}</p>
  </div>
</template>

<script>

import Inspire from './inspire';

export default {
  components:{
    Inspire,
  },
  mounted() {
    console.log(this.comments);
  },
}
</script>

<style scoped>
#id p{
  color: #ffffff;
}
</style>