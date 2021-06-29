<template>
  <jobs />
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import jobs from './components/jobs.vue'

export default defineComponent({
  name: 'App',
  components: { jobs }
})
</script>
