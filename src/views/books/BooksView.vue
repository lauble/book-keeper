<template>
  <div class="books">
    <h1>Books</h1>

    <input class="search" type="text" v-model="input" placeholder="Search books..." />

    <button @click="fetchData">Submit</button>

    <div v-for="book in books" :key="book.id" class="book">
      <router-link :to="{ name: 'book-details', params: { id: book.id } }">
        <h3>{{ book.volumeInfo.title }}</h3>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      input: '',
      books: [],
    }
  },
  methods: {
    fetchData() {
      fetch(`https://www.googleapis.com/books/v1/volumes?q=${this.input}`, {
        method: 'GET',
      })
        .then((res) => {
          res.json().then((data) => {
            this.books = data.items // returns array of objects
            console.log(data)
          })
        })
        .catch((err) => {
          console.error(err)
        })
    },
  },
}
</script>

<style>
a {
  text-decoration: none;
}

.books {
  padding: 20px;
}

.book h3 {
  background: #f4f4f4;
  padding: 10px;
  margin: 10px auto;
  border-radius: 10px;
  max-width: 600px;
  cursor: pointer;
  color: #444;
}

.search {
  margin: auto;
  border: 1px solid darkslateblue;
  border-radius: 30px;
  padding: 15px;
  width: 30%;
}
</style>
