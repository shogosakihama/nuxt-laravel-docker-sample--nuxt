<template>
  <div>
    <div class="p-5 bg-blue-100 border-b-8 border-white flex">
      <div
        @click="$store.commit('show')"
        class="header flex text-white font-midium sm:text-center md:text-left lg:text-left xl:text-left sm:text-4xl md:text-6xl lg:text-6xl xl:text-6xl"
      >
        Tailwindcss
      </div>

      <div class="ml-auto sm:hidden">
        <button
          class="mr-auto right-36 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-lg sm:mt-5 sm:invisible md:visible lg:visible xl:visible"
          type="button"
          @click="openModal"
        >
          新規登録/ログイン
        </button>
        <button
          class="right-10 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-lg sm:mt-5 sm:invisible md:visible lg:visible xl:visible"
          type="button"
          @click="$router.push({ path: '/post' })"
        >
          投稿する
        </button>
      </div>

      <div class="ml-auto sm:block md:hidden lg:hidden xl:hidden">
        <button
          class=" top-0 bg-blue-500 hover:bg-blue-700 text-white font-bold py-1 px-2 rounded-lg sm:mt-5 sm:visible md:invisible lg:invisible xl:invisible"
          type="button"
          @click="openModal"
        >
          メニュー
        </button>
      </div>
    </div>

    <div>
      <Modal v-if="modalFlag" @close-modal="closeModal" >
        <ul class="text-center border">
          <li class="border bg-white">モーダルの内容</li>
          <li class="border bg-white">モーダルの内容</li>
          <li class="border bg-white">モーダルの内容</li>
          <li class="border bg-white">モーダルの内容</li>
          <li class="border bg-white">モーダルの内容</li>
          <li class="border bg-white">
            <button @click="closeModal">
              閉じる
            </button>
          </li>
        </ul>
      </Modal>
    </div>

    <nuxt />
  </div>
</template>

<script>
import Modal from "~/components/modal.vue";
const axios = require("axios");
export default {
  components: {
    Modal
  },
  data: function() {
    return {
      modalFlag: false
    };
  },
  methods: {
    openModal() {
      this.modalFlag = true;
    },
    closeModal() {
      this.modalFlag = false;
    }
  }
};
</script>
