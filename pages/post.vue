<template>
  <div>
    <div class="max-w-xl m-auto mt-8">
      <div class="m-4">
        <label class="block text-gray-700 text-sm font-bold mb-2" for="title"
          >title</label
        >
        <input
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          id="title"
          type="text"
          v-model="title"
        />
      </div>
      <div class="m-4">
        <label class="block text-gray-700 text-sm font-bold mb-2" for="text"
          >text</label
        >
        <input
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          id="text"
          type="text"
          v-model="text"
        />
      </div>
      <div class="flex items-center justify-between">
        <button
          class="m-4 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
          type="button"
          @click="post"
        >
          投稿する
        </button>
      </div>
    </div>
  </div>
</template>

<script>
const axios = require("axios");
export default {
  data() {
    return {
      title: "",
      text: ""
    };
  },
  methods: {
    async post() {
      this.$axios
        .post("http://127.0.0.1:10080/api/post", {
        // .post("https://nuxt-laravel-docker.herokuapp.com/api/post", {
          title: this.title,
          text: this.text
        })
        .then(res => {
          console.log("test");
          location.href = "/";
        });
    }
  }
};
</script>

<style>
.container {
  height: 100vh;
  display: grid;
  grid-template-rows: 15% 1fr 10%;
  grid-template-columns: 15% 1fr 15%;
}
.header {
  grid-row: 1/2;
  grid-column: 1/4;
}
.item {
  grid-row: 2/3;
  grid-column: 2/3;
}
.footer {
  grid-row: 3/4;
  grid-column: 1/4;
}
.menus {
  grid-row: 2/4;
  grid-column: 1/2;
}
.modal {
  grid-row: 1/4;
  grid-column: 1/4;
}
</style>
