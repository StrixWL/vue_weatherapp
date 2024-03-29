<template>
    <div class="weather-card">
        <div class="section1">
            <img :src="icon" />
            <div class="city-infos">
                <h2>{{ city }}, {{ country }}</h2>
                <p>{{ date }}</p>
            </div>
        </div>
        <div class="section2">
            <div class="temperature">
                {{ temperature }}<span>°C</span>
            </div>
            <div class="condition">
                {{ weatherCondition }}
            </div>
        </div>
        <div class="section3">
            <div class="block">
                <div class="info">
                    <span><img class="info-icon" src="../assets/visibility.svg" />Visibility</span>
                    <span>{{ visibility }} KM</span>
                </div>
                <div class="info">
                    <span><img class="info-icon" src="../assets/temperature.svg" />Feels like</span>
                    <span>{{ feelsLike }} ° C</span>
                </div>
            </div>
            <div class="block">
                <div class="info">
                    <span><img class="info-icon" src="../assets/humidity.svg" />Humidity</span>
                    <span>{{ humidity }} %</span>
                </div>
                <div class="info">
                    <span><img class="info-icon" src="../assets/wind.svg" />Wind</span>
                    <span>{{ wind }} K/h</span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        cityData: {
            type: Object,
            required: true
        }
    },
    data() {
        return {
            apiKey: '064c662231bb47748b7114929242103',
            city: '',
            country: '',
            date: '',
            temperature: '',
            weatherCondition: '',
            visibility: '',
            feelsLike: '',
            humidity: '',
            wind: '',
            icon: ''
        };
    },
    mounted() {
        this.fetchWeatherData();
    },
    methods: {
        fetchWeatherData() {
            if (this.cityData.obj.city)
                Object.assign(this, this.cityData.obj);
            else {
                fetch(`https://api.weatherapi.com/v1/current.json?q=${this.cityData.name}&key=${this.apiKey}`)
                    .then(r => r.json())
                    .then(data => {
                        this.city = data.location.name
                        this.country = data.location.country
                        this.date = 'Monday 01/17/2024'
                        this.temperature = data.current.temp_c
                        this.weatherCondition = data.current.condition.text
                        this.visibility = data.current.vis_km
                        this.feelsLike = data.current.feelslike_c
                        this.humidity = data.current.humidity
                        this.wind = data.current.wind_kph
                        this.icon = "http:" + data.current.condition.icon.replace('64x64', '128x128')
                    })
            }
        }
    }
};
</script>

<style scoped>
.weather-card {
    height: 100%;
    display: flex;
    flex-direction: column;
    color: white
}

.section1 {
    /* background-color: lightcoral; */
    height: 32%;
    display: flex;
    justify-content: center;
}

.section2 {
    /* background-color: lightgreen; */
    height: 42%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.section3 {
    /* background-color: aqua; */
    height: 26%;
    overflow: hidden;
}

.section1 img {}

.city-infos {
    display: flex;
    flex-direction: column;
    gap: 0;
    align-items: start;
    justify-content: center;
    width: 60%;
}

.city-infos h2 {
    font-size: .2em;
    margin: .3em;
    margin-left: 1em;
    text-align: left;
}

.city-infos p {
    font-size: .13em;
    margin: 0;
    margin-left: 1.6em;
}

.temperature {
    height: 60%;
    font-size: 1.7em;
    display: flex;
    width: 100%;
    align-items: center;
    justify-content: center;
    margin-left: .2em;
}

.temperature span {
    font-size: .2em;
    position: relative;
    bottom: 1.3em;
}

.condition {
    font-size: .2em;
}

.block {
    display: flex;
    font-size: .175em;
    align-items: center;
    justify-content: center;
    gap: 1.4em;
    margin: .5em 0;
    font-weight: 200;
    font-family: Poppins;
}

.info {
    display: flex;
    gap: .5em;
    width: 40%;
    text-wrap: nowrap;
    justify-content: space-between;
}

.info span:nth-of-type(1) {
    display: flex;
    gap: .1em;
}

.info-icon {
    width: 1.4em;
}

</style>
