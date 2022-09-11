<template>
  <p class="job-order">Orderd by {{ order }}</p>
  <transition-group name="flip-list" class="job-list" tag="ul">
    <li class="job-list_item" v-for="job of orderedJobs" :key="job.id">
      <h2 class="job-list_item__title">
        <span>{{ job.title }} </span> in <span>{{ job.location }}</span>
      </h2>
      <p class="job-list_item__salary">{{ job.salary }} dollars</p>
      <p class="job-list_item__description">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Facilis,
        accusamus dolore. Mollitia, tempore! Blanditiis adipisci doloribus
        assumenda ullam accusantium sapiente ex debitis. A odio facilis, quas
        ipsa tempore aspernatur officia?
      </p>
    </li>
  </transition-group>
</template>

<script lang="ts">
import { computed, defineComponent, PropType } from "vue";
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
  setup(props) {
    const orderedJobs = computed(() => {
      return [...props.jobs].sort((job1: Job, job2: Job) => {
        return job1[props.order] > job2[props.order] ? 1 : -1;
      });
    });
    return { orderedJobs };
  },
});
</script>

<style lang="scss" scoped>
.flip-list-move {
  transition: transform 0.5s;
}
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
        & > span {
          background: white;
          text-transform: capitalize;
        }
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