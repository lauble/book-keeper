<script setup>
import BookDetailsCard from '../../components/BookDetailsCard.vue'
import { defineProps } from 'vue'

const props = defineProps({
  id: Number,
})
</script>

<template>
  <div class="book-details">
    <h1>Book details</h1>
    <p>The book id is {{ props.id }}</p>
  </div>
  <BookDetailsCard />
</template>

<style>
.book-details {
  padding: 20px;
}
</style>
