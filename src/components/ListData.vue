<template>
  <div>{{ message }}</div>
  <ul>
    <Person
      v-for="(item, index) in employees"
      :key="index"
      :name="item.name"
      :salary="item.salary"
      :id="item.id"
      :isVisible="item.isVisible"
      @show="toggleVisible"
      @delete="deleteEmployee"
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
  props: [],
  data() {
    return {
      message: "แสดงรายชื่อพนักงาน",
      employees: [
        {
          id: 0,
          name: "ก้อง",
          salary: 40000,
          isVisible: false,
        },
        {
          id: 1,
          name: "ยศ",
          salary: 45000,
          isVisible: false,
        },
        {
          id: 2,
          name: "ติน",
          salary: 45000,
          isVisible: false,
        },
      ],
    };
  },
  methods: {
    toggleVisible(id) {
      const newEmployee = this.employees.map((employee) => {
        if (employee.id === id) {
          const newEmployee = { ...employee, isVisible: !employee.isVisible };
          return newEmployee;
        }
        return employee;
      });
      this.employees = newEmployee;
    },
    deleteEmployee(id) {
      const newEmployee = this.employees.filter((employee) => {
        if (employee.id !== id) {
          return employee;
        }
      });
      this.employees = newEmployee;
    },
  },
};
</script>

<style>
</style>