<template>
    <div class = "container">
        <div class ="inner-container">
            <p>Paris, Ontario, Canada</p>
            <h2>{{ temperature }} <span>&#176;</span></h2>
            <h3>{{ weatherDescription }}</h3>
        <div v-if="showCloudy" class="weather-condition"><img src="../assets/cloudy.png" width = 200 height = 200 alt=""></div>
        <div v-if="showRainy" class="weather-condition"><img src="../assets/rainy.jpeg" width = 200 height = 200 alt=""></div>
        <div v-if="showStormy" class="weather-condition"><img src="../assets/storm.png" width = 200 height = 200 alt=""></div>
        </div>
    </div>
</template>
<script>

import axios from 'axios'
export default {
    data(){
        return {
            weather:{},
            weatherDescription:'',
            showCloudy: false,
            showStormy: false,
            showRainy: false,
            temperature: ''
        }
    },
    methods:{
        getWeatherData(){   
            axios.get().then(
                response => {
                console.log(response.data.weather[0].description)
                let mainDescription = response.data.weather[0].main;
                this.weatherDescription = response.data.weather[0].description;
                this.temperature = response.data.main.temp; 

                if (mainDescription == 'Clouds') {
                    this.showCloudy = true;
                }
                if (mainDescription == 'Rain') {
                        this.showRainy = true;
                    }
                if (mainDescription == 'Thunderstorm') {
                        this.showStormy = true;
                    }
                
                }
            ).catch(error => {console.log(error)})
        }
    },
    mounted() {
        this.getWeatherData();
    }

}
</script>

<style>
.container {
    width: 100%;
    display: flex;
    justify-content: center;
}
.inner-container {
    width: 50%;
    background-color: grey;
}

p {
    text-align:center;
}

h2 {
    text-align:center;
}

h3 {
    text-align:center;
}

.weather-condition {
    display: block;
    margin-left: auto;
    margin-right: auto;
    width: 50%;
}
</style>