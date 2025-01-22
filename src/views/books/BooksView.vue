<template>
  <div class="books">
    <h1>Books</h1>

    <input
      class="search"
      type="text"
      @keyup.enter="fetchData"
      v-model="input"
      placeholder="Search books..."
    />

    <button @click="fetchData">Search</button>
    <button @click="refresh">Refresh</button>
    <div v-show="searchInput" :style="{ padding: '10px', color: 'darkkhaki' }">
      {{ `results for '${searchInput}'` }}
    </div>

    <div v-for="book in books" :key="book.id" class="book">
      <router-link :to="{ name: 'book-details', params: { id: book.id } }">
        <h3>{{ book.volumeInfo.title }}</h3>
        <h5>Publisher: {{ book.volumeInfo.publisher }}</h5>
        <h5>{{ `${book.volumeInfo.publishedDate}`.slice(0, 4) }}</h5>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      input: '',
      searchInput: '',
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
            this.books = data.items // returns array of book objects
            this.searchInput = this.input
            this.input = ''
          })
        })
        .catch((err) => {
          console.error(err)
        })
    },
    refresh() {
      this.input = ''
      this.fetchData()
    },
  },
}
</script>

<style>
a {
  text-decoration: none;
  color: darkslategray;
}

button {
  cursor: pointer;
  border: 1px solid darkslateblue;
  border-radius: 30px;
  padding: 15px;
  font-family: 'Space Grotesk', sans-serif;
}

.books {
  padding: 50px;
}

.book {
  cursor: pointer;
  background: #f4f4f4;
  padding: 20px;
  margin: 10px auto;
  border-radius: 10px;
  max-width: 600px;
  color: #444;
  display: flex;
}

.search {
  margin: auto;
  border: 1px solid darkslateblue;
  border-radius: 30px;
  padding: 15px;
  width: 30%;
  font-family: 'Space Grotesk', sans-serif;
}
</style>
