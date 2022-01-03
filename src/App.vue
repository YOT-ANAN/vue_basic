<template>
  <section>
    <img v-bind:src="picture" v-bind:width="size" :height="size" />
    <!-- สามารถเขียน v-bind โดยใช้ : แทน -->
    <h1>ชื่อ-นามสกุล : {{ getFullName() }}</h1>
    <h1>อายุ : {{ age }} ปี</h1>
    <p>ที่อยู่ : <span v-html="address"></span></p>
    <a :href="social" target="_blank">facebook</a>
  </section>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      firstname: "Yot-anan",
      lastname: "Tioasakun",
      age: 23,
      address: "<strong>หาดใหญ่</strong>",
      picture: "https://cdn-icons-png.flaticon.com/512/5815/5815726.png",
      size: 200,
      social : "https://www.facebook.com/t.yotanan"
    };
  },
  methods: {
    getFullName() {
      return this.firstname + " " + this.lastname;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
