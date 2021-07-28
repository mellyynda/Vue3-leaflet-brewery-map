<template>
<div class="container">
<h3>My cool map</h3>
<div id="map1"></div>
</div>
</template>


<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  setup() {
    // const mymap = L.map('map1').setView([51.505, -0.09], 13);

    // return { mymap }
  }
})
</script>

<style>
#map1 { 
  height: 200px; 
}
</style>