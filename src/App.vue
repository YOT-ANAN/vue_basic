<template>
  <section>
    <img
      v-bind:src="picture"
      v-bind:width="size"
      :height="size"
      ref="imageEl"
    />
    <!-- bind attribute สามารถเขียน v-bind โดยใช้ : แทน -->
    <br />
    <form @submit.prevent="submitForm">
      ป้อนชื่อเล่น :
      <!-- <input type="text" v-on:input="setNickname" ref="nicknameEl" /> -->
      <input type="text" ref="nicknameEl" />
      <button type="submit">บันทึก</button>
    </form>
    <!-- event input โดยใช้ v-on -->
    <h1>ชื่อ-นามสกุล : {{ getFullName }}</h1>
    <h1>ชื่อเล่น: {{ nickname }}</h1>
    <h1>อายุ : {{ age }} ปี</h1>
    <div>เงินเดือน : {{ salary }}</div>
    <div>รายได้ต่อปี : {{ getIncome }}</div>
    <div>ตำแหน่งงงาน : {{ getDepartmnet }}</div>
    <div>Method : {{ getRandomByMethod() }}</div>
    <div>Method : {{ getRandomByMethod() }}</div>
    <hr />
    <div>Computed : {{ getRandomByComputed }}</div>
    <div>Computed : {{ getRandomByComputed }}</div>
    <div>
      <button @click="addSalary(5000)">เพิ่มเงินเดือน</button>
    </div>
    <div>
      <button @click="toggleVisible">
        {{ isVisible ? "ซ่อน" : "แสดงข้อมูลทั้งหมด" }}แสดงข้อมูลทั้งหมด
      </button>
    </div>
    <div v-show="isVisible === true">
      <p>ที่อยู่ : <span v-html="address"></span></p>
      <p>โซเชียลมีเดีย : <a :href="social" target="_blank">facebook</a></p>
      <p>งานอดิเรก :</p>
      <div v-if="hobby.length === 0">
        <p>ไม่มีงานอดิเรก</p>
      </div>
      <div v-else>
        <ul>
          <li v-for="(item, index) in hobby" :key="index">{{ item }}</li>
        </ul>
      </div>

      <p>ข้อมูลพื้นฐาน :</p>
      <ul>
        <li v-for="(item, key) in general" :key="key">
          {{ key }} : {{ item }}
        </li>
      </ul>
      <button @click="showData">ข้อมูลเพิ่มเติม</button>
      <button v-on:click="increment">เพิ่ม</button>
      <button v-on:click.right="incrementByValue(10)">เพิ่มทีละ 10</button>
      <!-- event สามารถเขียน v-on หรือลดรูปโดยใช้@ -->
    </div>
  </section>
</template>
<script>
export default {
  name: "App",
  data() {
    return {
      firstname: "Yot-anan",
      lastname: "Tioasakun",
      nickname: "",
      age: 23,
      address: "<strong>หาดใหญ่</strong>",
      picture: "https://cdn-icons-png.flaticon.com/512/5815/5815726.png",
      size: 200,
      social: "https://www.facebook.com/t.yotanan",
      hobby: ["เล่นเกมส์", "เล่นกีต้าร์", "เขียนโค้ด", "อ่านหนังสือ"],
      general: {
        gender: "ชาย",
        weight: 90,
        height: 170.5,
        status: false,
      },
      isVisible: false,
      salary: 40000,
    };
  },
  methods: {
    showData() {
      alert(`${this.firstname} ${this.lastname}`);
    },
    increment() {
      this.age++;
    },
    incrementByValue(value) {
      this.age += value;
    },
    setNickname(event) {
      console.log(event.target.value);
      this.nickname = event.target.value;
    },
    submitForm() {
      console.log(this.$refs.nicknameEl);
      this.nickname = this.$refs.nicknameEl.value;
    },
    toggleVisible() {
      this.isVisible = !this.isVisible;
    },
    getRandomByMethod() {
      return Math.random();
    },
    addSalary(value) {
      this.salary += value;
    },
  },
  computed: {
    getFullName() {
      return this.firstname + " " + this.lastname;
    },
    getRandomByComputed() {
      return Math.random();
    },
    getIncome() {
      return this.salary * 12;
    },
    getDepartmnet() {
      return this.salary > 35000 ? "Project Manager" : "Programer";
    },
  },
  watch: {
    salary(value) {
      if (value > 50000) {
        alert("เงินเดือนไม่ควรเกิน 50000");
        setTimeout(()=>{
          this.salary = 20000;
        },100)
      }
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
