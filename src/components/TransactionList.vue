<script setup>
defineProps({
  transactions: {
    type: Array,
    required: true,
  },
})

const emit = defineEmits(['transactionDeleted'])

const deleteTransaction = (id) => {
  emit('transactionDeleted', id)
}
</script>

<template>
  <h3>History</h3>
  <ul id="list" class="list">
    <li
      :class="transaction.amount < 0 ? 'minus' : 'plus'"
      v-for="transaction in transactions"
      :key="transaction.id"
    >
      {{ transaction.text }} <span>-${{ transaction.amount }}</span
      ><button class="delete-btn" @click="deleteTransaction(transaction.id)">x</button>
    </li>
  </ul>
</template>

<style scoped></style>
