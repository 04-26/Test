<template>
  <div>
    <button @click="toggle">点击切换</button>
    <test v-if="show" :ishow.sync="show"></test>
  </div>
</template>
<script>
import test from "./text";
export default {
  data() {
    return {
      msg: 12,
      show: true
    };
  },
  methods:{
    toggle(){
      this.show = !this.show
    },
    // change(bol){
    //   console.log(bol)
    //   this.show = bol
    // }
  },
  components: {
    test
  }
};
</script>
<style lang="css">
</style>