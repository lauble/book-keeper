<template>
  <div class="book-details">
    <h1>Book details</h1>
    <p>The book id is {{ id }}</p>
  </div>
</template>

<script>
export default {
  props: ['id'],
}
</script>

<style>
.book-details {
  padding: 20px;
}
</style>
