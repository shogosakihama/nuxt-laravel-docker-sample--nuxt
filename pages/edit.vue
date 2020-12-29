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
  data: function() {
    return {
      id: this.$route.query.id,
      title: this.title,
      text: this.text
    };
  },
  computed: {
    getId: function() {
      this.id = this.$route.query.id;
    }
  },
    methods: {
    async post() {
      this.$axios
        .post("http://127.0.0.1:10080/api/update", {
        // .post("https://nuxt-laravel-docker.herokuapp.com/api/post", {
          title: this.title,
          text: this.text,
          id: this.id
        })
        .then(res => {
          console.log("test");
          location.href = "/";
        });
    }
  }
};
</script>
