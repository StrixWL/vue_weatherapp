<template>
    <div class="swiper-container">
        <div class="swiper-wrapper">
            <div class="swiper-slide">
                <WeatherCard />
            </div>
            <div class="swiper-slide"></div>
            <div class="swiper-slide add-city">
                <div class="add-city__btn">
                    <img src="../assets/add.svg"/>
                    <h2>Add new location</h2>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Swiper from 'swiper';
import 'swiper/swiper-bundle.css';
import WeatherCard from './WeatherCard.vue'

export default {
    mounted() {
        new Swiper('.swiper-container', {
            pagination: {
                el: '.swiper-pagination',
            },
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
    height: 6em;
    max-height: 90%;
}

.swiper-slide {
    text-align: center;
    background: #fff;
    background-color: rgba(0, 0, 0, .4);
    border-radius: 4vh;
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

.add-city__btn:hover > img {
    transform: scale(1.1);
}

</style>