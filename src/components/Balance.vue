<!-- 余额组件 -->
<script setup>
const props = defineProps({
  total:{
    type:Number,
    required:true,
  }
})
</script>

<template>
  <h4>YOUR BALANCE</h4>
  <h1 id="balance">${{ total }}</h1>
</template>

<style lang="scss" scoped></style>
