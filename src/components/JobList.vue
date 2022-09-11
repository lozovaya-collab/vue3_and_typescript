<template>
  <p class="job-order">Orderd by {{ order }}</p>
  <ul class="job-list">
    <li class="job-list_item" v-for="job of jobs" :key="job.id">
      <h2 class="job-list_item__title">
        {{ job.title }} in {{ job.location }}
      </h2>
      <p class="job-list_item__salary">{{ job.salary }} dollars</p>
      <p class="job-list_item__description">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Facilis,
        accusamus dolore. Mollitia, tempore! Blanditiis adipisci doloribus
        assumenda ullam accusantium sapiente ex debitis. A odio facilis, quas
        ipsa tempore aspernatur officia?
      </p>
    </li>
  </ul>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import Job from "../types/Job";
import OrderTerm from "../types/OrderTerm";

export default defineComponent({
  name: "JobList",
  props: {
    jobs: {
      required: true,
      type: Array as PropType<Job[]>,
    },
    order: {
      required: true,
      type: String as PropType<OrderTerm>,
    },
  },
});
</script>

<style lang="scss" scoped>
.job {
  &-order {
    width: 80%;
    font-weight: 500;
  }
  &-list {
    list-style: none;
    padding: 0;
    width: 80%;
    &_item {
      background: white;
      padding: 15px;
      margin: 15px auto;
      &__title {
        background: white;
      }
      &__salary {
        background: white;
        color: rgb(26, 214, 26);
        font-weight: 600;
      }
      &__description {
        background: white;
      }
    }
  }
}
</style>