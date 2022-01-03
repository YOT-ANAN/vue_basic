<template>
  <section>
    <h1>ชื่อ-นามสกุล : {{ getFullName() }}</h1>
    <h1>อายุ : {{ age }} ปี</h1>
    <p>ที่อยู่ : <span v-html="address"></span></p>
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
