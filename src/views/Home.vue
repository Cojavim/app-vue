<template>
  <div class="home">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <v-btn block @click="loadDataFromServer" > Load data </v-btn>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";
export default {
  name: "Home",
  components: {
    // HelloWorld,
  },
  methods: {
    async loadDataFromServer(){
          const response = await fetch("http://localhost:5000/WeatherForecast/temperatures")
          console.log(await response.json())
      }
  },
};
</script>
