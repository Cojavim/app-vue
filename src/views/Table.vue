<template>
  <div id="Table">
    <v-data-table
      :headers="headers"
      :items="temperatures"
      :items-per-page="10"
      class="elevation-1"
    />
    <v-btn block @click="loadDataFromServer"> Reload data </v-btn>
  </div>
</template>

<script>
export default {
  mounted: async function () {
    this.loadDataFromServer();
  },
  methods: {
    async loadDataFromServer() {
      //   async await API
      try {
        const response = await fetch(
          "https://localhost:5001/WeatherForecast/temperatures"
        );
        this.temperatures = await response.json();
        console.log(this.temperatures);
      } catch (error) {
        console.log(error);
      }

      // then API
      //   fetch("https://localhost:5001/WeatherForecast/temperatures")
      //     .then((response) => response.json())
      //     .then((temperatures) => {
      //       this.temperatures = temperatures;
      //       console.log(this.temperatures);
      //     })
      //     .catch((e) => console.log(e));
    },
  },
  data() {
    return {
      headers: [
        {
          text: "Hour",
          align: "start",
          sortable: false,
          value: "hour",
        },
        { text: "Temperature", value: "temperature" },
      ],
      temperatures: [],
    };
  },
};
</script>

