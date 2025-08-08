<script setup>
    import { getTimePercentage } from '../utils';

    // Questo perché ho passato tutto impacchettato in un solo oggetto
    defineProps({
        // Tra tutti quelli passati usiamo solo data, quindi va bene "prendere" solo quello.
        data: Object
    })

    let snapshot = getTimePercentage()

</script>


<template>
    <section id="clocks">
        <!--i si usa anche per il testo italics ("corsivo") -->
        <p><i>Time remaining in different units.</i></p>
        <div class="clocks-grid">
            <!-- clock = years, months.. index = 0, 1, 2..-->
            <div class="card clock-card" v-for="(clock, index) in Object.keys(data)">
                <div class="circle">
                    <!--Assegna la classe pari al valore attuale della variabile clock dichiarando true la condizione.-->
                    <div class="ticker"
                    :class="{[clock] : true}">
                    </div>
                </div>
                <div>
                    <h5>{{ data[clock] }}</h5>
                    <p>{{ clock }}</p>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>

</style>
