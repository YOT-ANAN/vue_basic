<template>
  <div>ชื่อ : {{ name }}</div>
  <div>เงินเดือน : {{ salary }}</div>
</template>

<script>
export default {
  name: "Person",
  props: {
    name: {
      type: String,
      required: true,
    },
    salary: {
      type: Number,
      required: true,
    },
  },
};
</script>

<style>
</style>