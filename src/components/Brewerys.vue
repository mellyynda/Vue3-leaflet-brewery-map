<template>
  <ul>
    <li 
    v-for="brewery in brewerys" 
    :key="brewery.id">
      {{brewery.name}}, 
      <span class="state">{{ brewery.state }}</span>
    </li>
  </ul>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'
import { Bar } from '../types/Bar'

export default defineComponent({
  props: {
    brewerys: {
      required: true,
      type: Array as PropType<Bar[]>
    },
  },
})
</script>

<style>

</style>