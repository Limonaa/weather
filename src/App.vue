<template>
    <v-app>
        <div class="main">
            <v-card width="500">
                <v-card-title>
                    <v-text-field
                        v-model="searchPlace"
                        label="Miejscowość"
                        outlined
                        append-outer-icon="mdi-magnify"
                        @click:append-outer="search"
                    />
                </v-card-title>
                <v-card-text 
                v-if="temperature"
                >
                <v-row class="justify-center" width="auto">
                        <h1>{{ temperature }}°C</h1>
                </v-row>  
                </v-card-text>
            </v-card>
        </div>
    </v-app>
</template>

<script>
const weather = require('openweather-apis');

export default {
    name: "App",
    data() {
        return {
            city: "",
            searchPlace: "",
            result: null,
            temperature: ''
        }
    },
    methods: {
        search () {
            weather.setAPPID('801cee3159ef09adf0e4aa4f918488d8');
            weather.setCity(this.searchPlace);
            weather.setUnits('metric');

            weather.getTemperature((err, temperature) => {
                this.temperature = Math.round(temperature).toString();
            });
        }
    },
}
</script>

<style>
    .main {
        margin: auto;

    }
</style>