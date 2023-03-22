<script setup>
    import {useRoute,useRouter, RouterView} from "vue-router"
    import carsData from "../data.json"
        
    const route = useRoute()
    const router = useRouter()   //To use back function 
    //Getting the car object with the id of the url
    let {id} = route.params
    let car = carsData.find(car => car.id == id)
        
</script>
<template>
      <div class="container">
        <div v-if="car">
            <h1>The car</h1>
            <p>Make: {{ car.make }}</p>
            <p>Body: {{ car.body }}</p>
            <p>Price: ${{ car.price }}</p>
            <p>Year {{ car.year }}</p>
            <RouterView />
      <button @click="router.back">Go back</button>

        </div>

        <div v-else>
            <h1>Car not found</h1>
        </div>
    </div>
</template>
