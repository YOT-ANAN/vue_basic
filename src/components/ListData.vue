<template>
  <div>{{ message }}</div>
  <ul>
    <Person
      v-for="(item, index) in employees"
      :key="index"
      :name="item.name"
      :salary="item.salary"
    />
  </ul>
</template>

<script>
import Person from "./Person.vue";
export default {
  name: "ListData",
  components: {
    Person,
  },
  props: ["employees"],
  data() {
    return {
      message: "แสดงรายชื่อพนักงาน",
    };
  },
};
</script>

<style>
</style>