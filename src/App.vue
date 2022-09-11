<template>
  <div id="app">
    <div class="buttons-header">
      <button class="buttons-header_item" @click="handleClick('title')">
        order by title
      </button>
      <button class="buttons-header_item" @click="handleClick('location')">
        order by location
      </button>
      <button class="buttons-header_item" @click="handleClick('salary')">
        order by salary
      </button>
    </div>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import JobList from "./components/JobList.vue";
import Job from "./types/Job";
import OrderTerm from "./types/OrderTerm";

export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      { id: 0, title: "title 1", location: "location 1", salary: 100000 },
      { id: 1, title: "title 2", location: "location 2", salary: 200000 },
      { id: 2, title: "title 3", location: "location 3", salary: 300000 },
      { id: 3, title: "title 4", location: "location 4", salary: 400000 },
      { id: 4, title: "title 5", location: "location 5", salary: 500000 },
      { id: 5, title: "title 6", location: "location 6", salary: 600000 },
      { id: 6, title: "title 7", location: "location 7", salary: 700000 },
    ]);
    const order = ref<OrderTerm>("title");

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return {
      jobs,
      handleClick,
      order,
    };
  },
});
</script>

<style lang="scss">
.buttons-header {
  display: flex;
  justify-content: space-between;
  width: 30%;
  padding: 15px 0;
  &_item {
    cursor: pointer;
    background: rgb(133, 251, 86);
    border: 2px solid rgb(22, 204, 22);
    font-weight: 600;
    padding: 10px 15px;
    box-sizing: border-box;
    &:hover {
      background: rgb(188, 255, 162);
    }
  }
}
</style>
