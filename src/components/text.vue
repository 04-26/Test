<template>
  <div>
    <button @click="cancel">点击关闭</button>
    <div class="text">{{msg}}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      msg: 5555,
      isshow:true
    };
  },
  methods:{
    cancel(){
      this.$emit("update:ishow",false)
    }
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