<template>
  <div class="container m-auto max-w-full relative">
    <Navs class="header" />
    <div class="item self-center content-center pt-10">
      <ul v-for="(item, key) in json_data" :key="key" class="border-b">
        <div class="">
          <li class="font-bold p-2">{{ item.id }}</li>
          <li class="font-bold p-2">title: {{ item.title }}</li>
          <li class="font-bold p-2">text: {{ item.text }}</li>
        </div>
        <div class="flex justify-end">
          <li class="text-right btn">
            <button
              class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-t-lg sm:mt-5"
              type="button"
              @click="$router.push({ path: '/edit/', query: { id: item.id } })"
            >
              編集する
            </button>
          </li>
          <li class="text-right btn">
            <button
              class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-t-lg sm:mt-5"
              type="button"
              @click="
                $router.push({ path: '/remove/', query: { id: item.id } })
              "
            >
              削除する
            </button>
          </li>
        </div>
      </ul>
    </div>
    <div class="footer bg-gray-200"></div>
    <div class="modal sm:visible md:visible lg:visible xl:invisible"></div>
  </div>
</template>

<script>
const axios = require("axios");
export default {
  data: function() {
    return {
      id: "",
      text: "",
      json_data: [],
      modalFlag: true
    };
  },

  asyncData: async function({ $axios }) {
    let { data } = await $axios({
      method: "get",
      url: "http://localhost:10080/api/index"
      // url: "https://nuxt-laravel-docker.herokuapp.com/api/index"
    });
    return { json_data: data.posts };
  },
  methods: {
    doAction: function() {
      this.$store.state.isActive = !isActive;
    },
    openModal() {
      this.modalFlag = true;
    },
    closeModal() {
      this.modalFlag = false;
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
