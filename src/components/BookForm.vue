<template>
  <form v-on:submit.prevent="bookSubmit(bookTitle, bookAuthor)" class="" action="#" method="post">
    <input v-model="bookTitle" type="text" name="title" value="" placeholder="Book Title">
    <input v-model="bookAuthor" type="text" name="author" value="" placeholder="Book Author">
    <div id="checkbox">
    <label for="finishedReading">Finished Reading</label>
    <input type="checkbox" value="bookData.finishedReading" v-model="bookData.finishedReading" />
    </div>
    <label for="borrowed">borrowed</label>
    <input v-model="bookData.ownership" type="radio" name="borrowed" value="borrowed">
    <label for="bought">bought</label>
    <input v-model="bookData.ownership" type="radio" name="bought" value="bought">
    <button type="submit" name="button">Add Book</button>
  </form>
</template>

<script>
export default {
  name: "BookForm",
  props: ["books"],
  data() {
    return {
      bookTitle: "",
      bookAuthor: "",
      finishedReading: false,
      ownership: []
    };
  },
  methods: {
    bookSubmit(bookTitle, bookAuthor) {
      this.$emit("addBook", bookTitle, bookAuthor);
    }
  }
};
</script>

<style>
</style>
