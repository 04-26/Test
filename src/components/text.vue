<template>
  <div>
    <div class="text" v-for="(item,index) in test" :key="index">{{item}}</div>
  </div>
</template>

<script>
export default {
  props: {
    test: {
      type: Array,
      default(){
          return []
      }
    }
  },
  data() {
    return {
      msg: 5555
    };
  }
};
</script>
<style scoped>
.text {
  height: 200px;
  width: 200px;
  background-color: pink;
}
</style>