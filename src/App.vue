<template>
  <div class="app">
    <h1>Hello guys! <br> This is where the <a href="">magic</a> happens</h1>
    <p class="intro">Lorem ipsum dolor sit amet consectetur <a>adipisicing elit</a>. Veniam, exercitationem? Commodi beatae molestiae at. Libero corporis, cupiditate sapiente consequatur suscipit dolor quibusdam sunt mollitia expedita voluptas. Pariatur magnam illum quod.</p>
    <div class="flex-cont">
      <div class="left">
        <Brewerys v-if="showBars" :brewerys="brewerys" />
        <div v-else class="loading">loading...</div>
      </div>
      <div class="right">
        <Map />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import Brewerys from './components/Brewerys.vue'
import Map from './components/Map.vue'
import { Bar } from './types/Bar'
import axios from 'axios'

export default defineComponent({
  name: 'App',
  components: { Brewerys, Map },
  setup() {
    const showBars = ref(false)
    const brewerys = ref<Bar[]>()   
      
    axios.get('https://api.openbrewerydb.org/breweries')
      .then(res => {
        showBars.value = true
        brewerys.value = res.data
      })

    return { showBars, brewerys }  
  }
});
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Enriqueta:wght@700&family=Open+Sans:wght@300;400&display=swap');
/* general rules */


/* Typography */
a,
a:visited,
.state { color: #93291b; text-decoration: none; }

a:hover { text-decoration: underline }

h1 { text-align: center; font-family: 'Enriqueta', arial, serif; line-height: 1.25; margin: 0 0 10px; font-size: 40px; font-weight: bold; }

h1 a,
h1 a:visited { color: #333333 }

h1 a:hover { color: #93291b; text-decoration: none; }

p, 
li { color: #333333; font-family: "Open Sans",Arial,sans-serif; font-size: 16px; }

p {
  line-height: 1.5625; 
  margin-bottom: 15px;
  padding: 10px;
  font-weight: 300;
}

button>a { background-color: #93291b; border: 1px solid #333333; border-radius: 3px 3px 3px 3px; box-shadow: 0 0 1px #93291b inset; color: #f5f5f5; padding: 5px; }

button>a:hover { background-color: #be3523; border-radius: 3px 3px 3px 3px; text-decoration: none; }

/* layout */
.flex-cont {
  display: flex;
  gap: 20px;
}
.left,
.right {
  flex: 0 1 50%;
  max-width: 50%;
}


/* list */
ul {
  list-style: none;
  border: 0.5px solid #ddd;
  background: #fff;
  max-height: 400px;
  overflow: auto;
  /* custom scrollbar */
  scrollbar-color: #6969dd #e0e0e0;
  scrollbar-width: thin;
}

li {
  border-bottom: 0.5px solid #ddd;
  padding: 15px;   
  font-weight: 400;
}
li:last-child {
  border-bottom: none;
}
</style>
