<template>
  <div>
    <div>ชื่อ : {{ name }}</div>
    <div v-show="isVisible">
      <div>เงินเดือน : {{ salary }}</div>
    </div>
    <div>
      <button @click="showDescription(id)">แสดงข้อมูล</button>
      <button @click="deleteEmployee(id)">ลบข้อมูล</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Person",
  props: {
    id: {
      type: Number,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    salary: {
      type: Number,
      default: 15000,
    },
    isVisible: {
      type: Boolean,
    },
  },
  methods: {
    showDescription(id) {
      this.$emit("show", id);
    },
    deleteEmployee(id) {
      this.$emit("delete", id);
    },
  },
};
</script>

<style>
</style>