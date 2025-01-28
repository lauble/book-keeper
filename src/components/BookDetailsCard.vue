<template>
  <div class="card" v-show="book">
    <h2>{{ book.title }}</h2>
    <h2 v-show="book.subtitle">Subtitle: {{ book.subtitle }}</h2>
    <p class="book-description">{{ book.description }}</p>
    <h3>Publisher: {{ book.publisher }}</h3>
    <h3>Author(s): {{ book.authors.join(',') }}</h3>
  </div>
  <!-- <button @click="fetchData">Test</button> -->
</template>

<script>
// import { defineProps } from 'vue'

const API_KEY = import.meta.env.VITE_GOOGLE_API_KEY
// const props = defineProps({
//   id: String,
// })

export default {
  name: 'BookDetailsCard',
  data() {
    return {
      id: this.$route.params.id,
      book: {},
    }
  },
  created() {
    this.fetchData()
  },
  methods: {
    fetchData() {
      fetch(`https://www.googleapis.com/books/v1/volumes?q=${this.id}&key=${API_KEY}`, {
        method: 'GET',
      }).then((res) => {
        res.json().then((data) => {
          this.book = data.items[0].volumeInfo
          console.log(this.book)
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
  padding: 10px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 40%;
  height: fit-content;
  font-family: 'Space Grotesk', sans-serif;
}

.book-description {
  padding: 10px;
  background-color: antiquewhite;
  border-radius: 10px;
}
</style>
