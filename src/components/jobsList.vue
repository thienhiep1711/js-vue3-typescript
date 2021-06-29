<template>
  <div class="job-list">
    Order by: {{ order }}
    <transition-group name="list" tag="ul">
      <li v-for="job in orderedJobs" :key="job.id">
        {{ job.title }},  {{ job.location }},  {{ job.salary }}
      </li>
    </transition-group>
  </div>
</template>

<script lang="ts">
import Job from '@/types/Job'
import OrderTerm from '@/types/OrderTerm'
import { computed, defineComponent, PropType } from 'vue'

export default defineComponent({
  props: {
    jobs: {
      required: true,
      type: Array as PropType<Job[]>
    },
    order: {
      required: true,
      type: String as PropType<OrderTerm>
    }
  },
  setup (props) {
    const orderedJobs = computed(() => {
      return [...props.jobs].sort((a: Job, b:Job) => {
        return a[props.order] > b[props.order] ? 1 : -1
      })
    })
    return { orderedJobs }
  }
})
</script>
