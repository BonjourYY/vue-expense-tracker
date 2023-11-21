<script setup>
const props = defineProps({
  transactions:{
    type:Array,
    required:true,
  }
})

const emits = defineEmits(['transactionDeleted'])

const deleteTransaction = (id)=>{
  emits('transactionDeleted',id)
}
</script>

<template>
  <h3>History</h3>
  <ul id="list" class="list">
    <li
      v-for="{id,text,amount} in transactions"
      :key="id"
      :class="amount < 0 ? 'minus':'plus'">
      {{text}} <span>${{ amount }}</span
      ><button @click="deleteTransaction(id)" class="delete-btn">x</button>
    </li>
  </ul>
</template>

<style lang="scss" scoped></style>
