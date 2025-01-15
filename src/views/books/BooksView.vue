<template>
  <div class="books">
    <h1>Books</h1>
    <div v-for="book in books" :key="book.id" class="book">
      <router-link :to="{ name: 'book-details', params: { id: book.id } }">
        <h3>{{ book.title }}</h3>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      books: [
        {
          id: 1,
          title: 'Be Ready When The Luck Happens',
          author: 'Ina Garten',
          year: 2024,
          details: 'Lorem, ipsum dolor sit amet consectetur adipisicing elit.',
        },
        {
          id: 2,
          title: 'Strongmen',
          author: 'Ruth Ben-Ghiat',
          year: 2020,
          details: 'Lorem, ipsum dolor sit amet consectetur adipisicing elit.',
        },
        {
          id: 3,
          title: 'Thinking Fast and Slow',
          author: 'Daniel Kahneman',
          year: 2011,
          details: 'Lorem, ipsum dolor sit amet consectetur adipisicing elit.',
        },
      ],
    }
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
</style>
