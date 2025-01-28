<script setup>
import BookDetailsCard from '../../components/BookDetailsCard.vue'
import { defineProps } from 'vue'

const props = defineProps({
  id: String,
})
</script>

<template>
  <div class="book-details">
    <h2>Book details</h2>
    <!-- <p>The book id is {{ props.id }}</p> -->
  </div>
  <BookDetailsCard />
</template>

<style>
.book-details {
  padding: 20px;
  font-family: 'Space Grotesk', sans-serif;
}
</style>
