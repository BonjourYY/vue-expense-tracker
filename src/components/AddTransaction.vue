<script setup>
import { ref } from 'vue';
import { useToast } from 'vue-toastification'
const toast = useToast()

const text = ref(null)
const amount = ref(null)
const emits = defineEmits(['transactionSubmitted'])

const onSubmit = () => {
  if (!text.value || !amount.value) {
    toast.error("所有字段必须填写！")
    return;
  }

  const transactionData = {
    text:text.value,
    amount:amount.value
  }

  emits('transactionSubmitted',transactionData)

  text.value = null;
  amount.value = null;
}
</script>

<template>
  <h3>Add new transaction</h3>
  <form id="form" @submit.prevent="onSubmit">
    <div class="form-control">
      <label for="text">Text</label>
      <input type="text" id="text" placeholder="Enter text..." v-model="text" />
    </div>
    <div class="form-control">
      <label for="amount"
        >Amount <br />
        (negative - expense, positive - income)</label
      >
      <input
        type="number"
        id="amount"
        placeholder="Enter amount..."
        v-model="amount" />
    </div>
    <button class="btn">Add transaction</button>
  </form>
</template>

<style lang="scss" scoped></style>
