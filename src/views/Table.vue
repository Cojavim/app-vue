<template>
    <div id="Table">
        <v-data-table
        :headers="headers"
        :items="temperatures"
        :items-per-page="10"
        class="elevation-1"
    ></v-data-table>
    <v-btn block @click="loadDataFromServer" > Reload data </v-btn>
    </div>
</template>

<script>
export default {
    mounted: async function(){
        this.loadDataFromServer();
    },
    methods: {
        async loadDataFromServer(){
            const response = await fetch("https://localhost:5001/WeatherForecast/temperatures")
            let lStringified = JSON.stringify(await response.json());
            this.temperatures = JSON.parse(lStringified)
            // console.log(await response.json())
            console.log(this.temperatures)
        }
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
        temperatures: []
        };
    },
}
</script>

<style>

</style>