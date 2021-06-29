<template>
  <button @click="handleClick('title')">order by title</button>
  <button @click="handleClick('salary')">order by salary</button>
  <button @click="handleClick('locations')">order by location</button>
  <jobs-list :jobs="jobs" :order="order" />
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import Job from '../types/Job'
import OrderTerm from '../types/OrderTerm'
import jobsList from './jobsList.vue'

export default defineComponent({
  components: { jobsList },
  setup () {
    const jobs = ref<Job[]>([
      { title: 'Hiep Nguyen', location: 'Ha Noi', salary: 50000, id: '1' },
      { title: 'Luan Nguyen', location: 'HCM', salary: 40000, id: '2' }
    ])
    const order = ref<OrderTerm>('title')
    const handleClick = (term: OrderTerm) => {
      order.value = term
    }
    return { jobs, handleClick, order }
  }
})
</script>
