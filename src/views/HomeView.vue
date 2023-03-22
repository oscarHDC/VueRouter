    <template>
     <main class="container">
      <h1>Our cars</h1>
      <select v-model="make" @change="handleChange">
        <option value="All">All</option>
        <option value="Chevrolet">Chevy</option>
        <option value="Porsche">Porsche</option>
        <option value="Audi">Audi</option>  
      </select>
      <div class="cards">
        <div v-for="car in cars" :key="car" class="card" @click="router.push(`/car/${car.id}`)">
          <h1>{{ car.make }}</h1>
          <p>${{ car.price }}</p>
        </div>
      </div>
     </main>
    </template>


<script setup>
  import carsData from "../data.json"
  import { ref, watch } from "vue";
  import { useRouter } from "vue-router";

  const router = useRouter()
  const cars = ref(carsData)
  const make = ref("")

  watch(make, () => {
    if(make.value){
        if(make.value === "All") cars.value = carsData;
        else{
            cars.value = carsData.filter(c => c.make === make.value)
        }
    }
  })

  //Add query so if user select a type of car the url change to http://localhost:5173/?make=TypeOfCar
  //This doesnt change the app at all, it improves the UX
  const handleChange = () => {
    router.push({query: {make: make.value}})
  }

</script>


<style scoped>
  .cards {
  display: flex;
  width: 1000px;
  flex-wrap: wrap;
  margin-top: 50px;
  justify-content: center;
}
.card {
  box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.207);
  padding: 15px;
  width: 150px;
  margin-right: 15px;
  cursor: pointer;
  margin-bottom: 20px;
}

</style>
