<template>
  <div id="app">
    <select class="select" v-model="selected">
      <option v-for="book in books" :value="book.id" :key="book.id">
        {{ book.title }}
      </option>
    </select>
    <Book :id="books[selected].id" :title="books[selected].title" :author="books[selected].author" :age-group="books[selected].ageGroup" :cover-image="books[selected].coverImage" :cover-image-path="coverImagePath"></Book>
  </div>
</template>

<script>
import Book from "./components/Book.vue";

const dataUrl = 'book-data.json';

export default {
  name: "app",
  data() {
    return {
      books: [{}],
      selected: 0,
      coverImagePath: './img/'
    };
  },
  components: {
    Book
  },
  mounted() {
    this.loadData();
  },
  methods: {
    loadData: function() {
      var vue = this;
      fetch(dataUrl)
        .then(response => {
          return response.json().then(data => {
            if (response.ok) {
              return data;
            } else {
              return Promise.reject({ status: response.status, data });
            }
          });
        })
        .then(data => {
          vue.books = data.books;
        })
        .catch(error => {
          /* eslint-disable no-alert */
          alert("Oops! An error occurred.");
          /* eslint-disable no-console */
          console.log(error);
        });
    }
  }
};
</script>

<style>
#app {
  font-family: Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #4b5055;
}
.select {
  border: 1px solid #d5d6d6;
  border-radius: 20px;
  color: #4b5055;
  display: block;
  font-size: 1.1rem;
  height: 40px;
  margin: 2rem auto;
}
</style>
