<script setup>
import { computed } from 'vue';

  const {data, lifeExpectancy} = defineProps({
    data: Object,
    lifeExpectancy: Object,
  })

  // Computed fa si che l'assegnazione sia ricacolata quando le dipendenze (variabili all'interno) cambiano.
  // Crea e ritorna un array lungo il parametro di Array (usando lo spread operator) e le chiavi necessarie ad iterare
  const yearsArr = computed(() => [...Array(lifeExpectancy.value).keys()])
  const weeksArr = [...Array(52).keys()]
  const weekNum = computed(() => lifeExpectancy.value * 52 -  parseInt(data.value['weeks']))
  const finalWeek = computed(() => lifeExpectancy.value * 52)

  // Sia per computed che per ref il valore viene inserito nel campo .value
  function getWeeksArr(wksArr, yrIndex) {
    return wksArr.map((val, valIndex) => {
        // L'obiettivo è capire come colorare i quadratini in base al punto della vita in cui si trovano.
        const currWeek = yrIndex * 52 + valIndex
        const dotStyle = currWeek == finalWeek.value - 1
            ? " death"
            : currWeek < weekNum.value
            ? " solid"
            : currWeek == weekNum.value
            ? " pulse"
            : ""
        return {week: val, currWeek, dotStyle}
    })
  }
</script>

<template>
    <section id="caldendar">
        <p><i>Each square of dots represents 52 weeks / 1 year of your life.</i></p>
        <div class="dozen-grid">
            <div class="year-grid" v-for="(year, yearIndex) in yearsArr" :key="yearIndex">
                <!--Week non è solo più chiave / valore, ma contiene le informazioni necessarie per colorare i quadratini correttamente-->
                <div 
                    class="dot"
                    v-for="(week, weekIndex) in getWeeksArr(weeksArr, yearIndex)"
                    :key="weekIndex"
                    :class="week.dotStyle">
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>

</style>
