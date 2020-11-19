<template>
    <div id="chart">
        <v-container fluid>
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
            <v-btn block @click="loadDataFromServer" > Reload data </v-btn>
        </v-container>
    </div>
</template>

<script>
    const gradients = [
        ['#222'],
        ['#42b3f4'],
        ['red', 'orange', 'yellow'],
        ['purple', 'violet'],
        ['#00c6ff', '#F0F', '#FF0'],
        ['#f72047', '#ffd200', '#1feaea']
    ]

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
                this.temps = [],
                this.hours = [],
                this.temperatures.forEach(element => {
                    this.temps.push(element.temperature)
                    this.hours.push(element.hour)
                });
            }
        },
        data: () => ({
        lineCap: 'round',
        gradientDirection: 'top',
        gradient: gradients[5],
        value: [0, 2, 5, 9, 5, 10, 3, 5, 0, 0, 1, 8, 2, 9, 0],
        labels:[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14],
        temps: [],
        hours: [],
        gradients,
        temperatures: []
        })
    }
</script>

<style>

</style>