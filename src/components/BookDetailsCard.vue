<template>
  <div class="card">
    <h1>Book Details Card</h1>
    <p>This is the book details card. The id is {{ id }}</p>
    <button @click="fetchData">Test</button>
  </div>
</template>

<script>
import { defineProps } from 'vue'

const API_KEY = import.meta.env.VITE_GOOGLE_API_KEY
// const props = defineProps({
//   id: String,
// })

export default {
  name: 'BookDetailsCard',
  data() {
    return {
      id: this.$route.params.id,
      books: [],
    }
  },
  methods: {
    fetchData() {
      fetch(`https://www.googleapis.com/books/v1/volumes?q=${this.id}&key=${API_KEY}`, {
        method: 'GET',
      }).then((res) => {
        res.json().then((data) => {
          console.log(data)
          this.books = data.items
        })
      })
    },
  },
}
</script>

<style>
.card {
  margin: auto;
  border: 1px solid darkslategray;
  border-radius: 40px;
  background-color: darkkhaki;
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 50%;
}
</style>
