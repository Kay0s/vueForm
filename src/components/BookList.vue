<template>
  <div>
    <h1>{{title}}</h1>
    <input type="text" placeholder="" v-model="searchInput">
    <ul>
      <book-item v-for='book in books' :key='book.id' :book='book'></book-item>
    </ul>
    <hr><h2>Filtered Books by Ownership</h2>
    <select v-model="holding">
      <option v-for='filter in filters' :key='filter.id' :filter='filter'>{{ filter }}</option>
    </select>
    <ul>
      <book-item v-for='book in filteredBooks' :key='book.id' :book='book'></book-item>
    </ul>
    <br><hr>
    <book-form @addBook='appendBook'></book-form>
  </div>
</template>

<script>
import _ from "lodash";
import BookItem from "./BookItem";
import BookForm from "./BookForm";

export default {
  name: "BookList",
  data() {
    return {
      title: "All Books",
      states: ["Want to Read", "Read", "Reading"],
      filters:["bought", "borrowed"],
      holding: "bought",
      books: [
        { title: "Self-Reliance", author: "Ralph Waldo Emerson", finishedReading: true, ownership: "borrowed" },
        { title: "American Gods", author: "Neil Gaiman", finishedReading: false, ownership: "bought" },
        { title: "Amusing Ourselves to Death", author: "Neil Postman", finishedReading: true, ownership:"borrowed" }
      ]
    
    };
  },
  computed: {
    filteredBooks() {
      return _.filter(this.books, ["ownership", this.holding]);
    }

  },
  components: {
    BookItem,
    BookForm
  },
  methods: {
    appendBook(bookData) {
      this.books.push({ title: bookData.bookTitle, author: bookData.bookAuthor, finishedReading: bookData.finishedReading, ownership: bookData.ownership });
    }
  }
};
</script>

<style>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: block;
  margin: 0 10px;
}
</style>
