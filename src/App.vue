<script setup>
  import Layout from './components/layouts/Layout.vue';
  import Hero from './components/Hero.vue';
  import Clocks from './components/Clocks.vue';
  import Calendar from './components/Calendar.vue'
  import Summary from './components/Summary.vue';

  import {calculateTimeLeft} from './utils'

  const birthDate = '1991-07-18'
  const lifeExpectancy = 80
  const name = 'Alberto'
  const data = calculateTimeLeft(birthDate, lifeExpectancy)
  console.log(data)

  // Si possono passare i props anche impacchettati in un oggetto tramite v-bind.

  const totalProps = {
    birthDate,
    lifeExpectancy,
    name,
    data
  }

  console.log(totalProps)
</script>

<template>
  <Layout>
    <Hero :name="name" :data="data" />
    <!--Il v-bind si passa senza i due punti davanti, in quanto ci aspettiamo già un pacchetto con i props!-->
    <Clocks v-bind="totalProps" />
    <Calendar/>
    <Summary/>
  </Layout>
</template>

<style scoped>

</style>
