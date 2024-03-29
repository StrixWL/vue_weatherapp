<template>
    <div class="weather-card">
        <div class="section1">
            <img src="../assets/sun.svg" />
            <div class="city-infos">
                <h2>Rabat, Morocco</h2>
                <p>Monday 01/17/2024</p>
            </div>
        </div>
        <div class="section2"></div>
        <div class="section3"></div>
    </div>
</template>

<script>
</script>

<style scoped>

.weather-card {
    widows: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    color: white
}

.section1 {
    /* background-color: lightcoral; */
    height: 29%;
    display: flex;
    justify-content: center;
}

.section2 {
    background-color: lightgreen;
    height: 42%;
}

.section3 {
    background-color: aqua;
    height: 29%;
}

.section1 img {
    width: 24%;
}

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

</style>
