<template>
  <section>
    <img v-bind:src="picture" v-bind:width="size" :height="size" />
    <!-- สามารถเขียน v-bind โดยใช้ : แทน -->
    <h1>ชื่อ-นามสกุล : {{ getFullName() }}</h1>
    <h1>อายุ : {{ age }} ปี</h1>
    <p>ที่อยู่ : <span v-html="address"></span></p>
    <p>โซเชียลมีเดีย : <a :href="social" target="_blank">facebook</a></p>
    <p>งานอดิเรก :</p>
    <ul>
      <li v-for="(item, index) in hobby" :key="index">{{ item }}</li>
    </ul>
    <p>ข้อมูลพื้นฐาน :</p>
    <ul>
      <li v-for="(item, key) in general" :key="key">{{ key }} : {{ item }}</li>
    </ul>
    <button @click="showData">ข้อมูลเพิ่มเติม</button>
    <button v-on:click="increment">เพิ่ม</button>
    <button v-on:click="incrementByValue(10)">เพิ่มทีละ 10</button>

    <!-- สามารถเขียน v-on หรือลดรูปโดยใช้@ -->
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
      social: "https://www.facebook.com/t.yotanan",
      hobby: ["เล่นเกมส์", "เล่นกีต้าร์", "เขียนโค้ด"],
      general: {
        gender: "ชาย",
        weight: 90,
        height: 170.5,
        status: false,
      },
    };
  },
  methods: {
    getFullName() {
      return this.firstname + " " + this.lastname;
    },
    showData() {
      alert(`${this.firstname} ${this.lastname}`);
    },
    increment() {
      this.age++;
    },
    incrementByValue(value) {
      this.age+=value;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>
