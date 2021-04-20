<template>
  <form v-on:submit.prevent="bookSubmit(bookData)" class="" action="#" method="post">
    <input v-model="bookData.bookTitle" type="text" name="title" value="" placeholder="Book Title">
    <input v-model="bookData.bookAuthor" type="text" name="author" value="" placeholder="Book Author">
    <div id="checkbox">
    <label for="finishedReading">Finished Reading</label>
    <input type="checkbox" value="bookData.finishedReading" v-model="bookData.finishedReading" />
    </div>
    <label for="borrowed">borrowed</label>
    <input v-model="bookData.ownership" type="radio" name="borrowed" value="borrowed">
    <label for="bought">bought</label>
    <input v-model="bookData.ownership" type="radio" name="bought" value="bought">
    <button type="submit" name="button" v-on:submit.prevent="bookSubmit(bookData)">Add Book</button>
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
      bookData: "",
      finishedReading: false,
      ownership: []
    };
  },
  methods: {
    bookSubmit(bookData) {
      this.$emit("addBook", bookData);
    }
  }
};
</script>

<style>
</style>
