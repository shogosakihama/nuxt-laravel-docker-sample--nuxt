<template>
  <div>

  </div>
</template>

<script>
const axios = require("axios");
export default {
  data() {
    return {
      title: "",
      text: "",
      id: ""
    };
  },

  mounted(){
      this.id = this.$route.query.id;
      this.$axios
        .post("http://localhost:10080/api/remove", {
          id: this.id
        })
        .then(res => {
          console.log("test");
          location.href = "/";
        });
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
