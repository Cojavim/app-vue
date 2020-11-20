<template>
  <div id="chart">
    <v-sheet
      v-if="!loaded"
      :color="`grey ${theme.isDark ? 'darken-2' : 'lighten-4'}`"
      class="pa-1"
    >
      <v-skeleton-loader
        class="mx-auto"
        max-width="auto"
        type="card"
      ></v-skeleton-loader>
    </v-sheet>
    <v-container v-else fluid>
      <v-sparkline
        :value="temps"
        :labels="hours"
        :gradient="gradients[5]"
        :smooth="10 || false"
        :padding="8"
        :line-width="2"
        :stroke-linecap="lineCap"
        :gradient-direction="gradientDirection"
        auto-draw
      ></v-sparkline>

      {{ myComputed }}
      {{ myData.asdasd && myData.asdasd.asdas }}
      <v-btn block @click="loadDataFromServer"> Reload data </v-btn>
    </v-container>
  </div>
</template>

<script>
const gradients = [
  ["#222"],
  ["#42b3f4"],
  ["red", "orange", "yellow"],
  ["purple", "violet"],
  ["#00c6ff", "#F0F", "#FF0"],
  ["#f72047", "#ffd200", "#1feaea"],
];

export default {
  mounted: async function () {
    this.loadDataFromServer();
  },
  methods: {
    async loadDataFromServer() {
      this.loaded = false;
      const response = await fetch(
        "https://localhost:5001/WeatherForecast/temperatures"
      );
      this.temperatures = await response.json();

      console.log(this.temperatures);
      this.temps = this.temperatures.map((e) => e.temperature);
      this.hours = this.temperatures.map((e) => e.hour);

      function delay(ms) {
        return new Promise((resolve) => setTimeout(resolve, ms));
      }

      await delay(5000);
      this.loaded = true;
    },
  },
  inject: {
    theme: {
      default: { isDark: true },
    },
  },
  computed: {
    myComputed() {
      // C#
      //   var test = myProp ?? someOtherValue;
      //js
      //   var test = myProp || someOtherValue;

      // C#
      //   var test = myData?.asdasd?.asdas;
      //js
      //   var test = myData && myData.asdasd && myData.asdasd.asdas;
      //   var test = myData?.asdasd?.asdas;

      return this.myData?.asdasd?.asdas;
    },
  },
  data: () => ({
    loaded: false,
    lineCap: "round",
    gradientDirection: "top",
    gradient: gradients[5],
    myData: {
      value: [0, 2, 5, 9, 5, 10, 3, 5, 0, 0, 1, 8, 2, 9, 0],
      labels: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14],
      asdasd: {
        asdas: "asdasdsa",
      },
    },
    temps: [],
    hours: [],
    gradients: undefined,
    temperatures: [],
  }),
};
</script>

<style>
</style>