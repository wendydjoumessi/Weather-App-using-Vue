<script setup>
 import SearchInput from './components/SearchInput.vue';
 import { ref } from 'vue'
import WeatherCard from './components/WeatherCard.vue';
 

 const places = ref([]);

 const addPlace = (data) => {
  places.value.push(data);
 }

 const deletePlace =  (name)=>{
  if( confirm('Are you sure you')) {
  places.value = places.value.filter(p => p.location.name !== name)
  }
 }
</script>
<template>
  <main>
    <!-- Date -->
    <div class="text-center mb-6">
      {{ new Date().toLocaleDateString('en-us', {
        weekday: 'long',
        year : 'numeric',
        month : 'long',
        day : 'numeric'
        }) 
      }}
    </div>

    <!-- search -->
    <div>
      <SearchInput @place-data="addPlace"/>
    </div>

    <!-- Weather cards -->

    <div class="grid grid-cols-4 gap-4">
      <div v-for="(place, idx) in places" :key="idx">
       <WeatherCard :place="place" @delete-place="deletePlace"/>
     </div>
    </div>

  </main>
</template>
