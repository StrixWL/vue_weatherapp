<template>
    <div class="swiper-container">
        <div class="swiper-wrapper">
            <div v-for="(city, index) in cities" :key="index" class="swiper-slide">
                <WeatherCard :cityData="city" />
            </div>
            <div class="swiper-slide add-city">
                <button :onClick="addCityButton" class="add-city__btn">
                    <img src="../assets/add.svg" />
                    <h2>Add new location</h2>
                </button>
                <input class="city-input" placeholder="Location name" type="text" v-model="inputValue" />
            </div>
        </div>
    </div>
</template>

<script>
import Swiper from 'swiper';
import 'swiper/swiper-bundle.css';
import WeatherCard from './WeatherCard.vue'

export default {
    methods: {
        addCityButton() {
            fetch(`https://api.weatherapi.com/v1/current.json?q=${this.inputValue}&key=${this.apiKey}`)
                .then(r => r.json())
                .then(data => {
                    if (data.location) {
                        this.cities.push({
                            name: data.location.name,
                            obj: {
                                city: data.location.name,
                                country: data.location.country,
                                date: 'Monday 01/17/2024',
                                temperature: data.current.temp_c,
                                weatherCondition: data.current.condition.text,
                                visibility: data.current.vis_km,
                                feelsLike: data.current.feelslike_c,
                                humidity: data.current.humidity,
                                wind: data.current.wind_kph,
                                icon: "http:" + data.current.condition.icon.replace('64x64', '128x128')
                            }
                        })
                        this.$nextTick(() => {
                            this.swiper.update();
                        });
                    }
                    else {
                        console.log("nop")
                    }
                })
            this.inputValue = ''
        }
    },
    data() {
        return {
            cities: [
                {
                    name: "Rabat",
                    obj: {}
                },
                {
                    name: "Oujda",
                    obj: {}
                }
            ],
            inputValue: '',
            apiKey: '064c662231bb47748b7114929242103'
        }
    },
    mounted() {
        this.swiper = new Swiper('.swiper-container', {
            spaceBetween: 20
        });
    },
    components: {
        WeatherCard
    }
};
</script>

<style scoped>
.swiper-container {
    font-size: 10vh;
    width: 4em;
    height: 5.5em;
    max-height: 90%;
}

.swiper-slide {
    text-align: center;
    background: #fff;
    background-color: rgba(0, 0, 0, .4);
    border-radius: 4vh;
    transition: all .2s;
}

.add-city {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    color: white;
}

.add-city img {
    height: 1.4em;
    transition: transform .1s;
}

.add-city h2 {
    font-size: 18px;
    font-size: .2em;
}

.add-city__btn {
    cursor: pointer;
}

.add-city__btn:hover>img {
    transform: scale(1.1);
}

.city-input {
    border: none;
    height: 2em;
    border-radius: 1em;
    width: 10em;
    padding: 0 1.2em;
    text-align: center
}
</style>