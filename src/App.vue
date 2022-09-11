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
      { id: 1, title: "farm worker", location: "lon lon ranch", salary: 30000 },
      { id: 2, title: "quarryman", location: "death mountain", salary: 40000 },
      {
        id: 3,
        title: "flute player",
        location: "the lost woods",
        salary: 35000,
      },
      { id: 4, title: "fisherman", location: "lake hylia", salary: 21000 },
      {
        id: 5,
        title: "prison guard",
        location: "gerudo valley",
        salary: 32000,
      },
      {
        id: 6,
        title: "Yandex",
        location: "Moscow",
        salary: 42000,
      },
      {
        id: 7,
        title: "Sber",
        location: "Samara",
        salary: 12000,
      },
      {
        id: 8,
        title: "Ozon",
        location: "Saint-Petersburg",
        salary: 32500,
      },
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
