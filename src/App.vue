<script setup>
  import Layout from './components/layouts/Layout.vue';
  import Hero from './components/Hero.vue';
  import Clocks from './components/Clock.vue';
  import Calendar from './components/Calendar.vue'
  import Summary from './components/Summary.vue';

  import {calculateTimeLeft} from './utils'

  const birthDate = '1991-07-18'
  const lifeExpectancy = 80
  const name = 'Alberto'
  const data = calculateTimeLeft(birthDate, lifeExpectancy)
  console.log(data)
</script>

<template>
  <Layout>
    <Hero :name="name" :data="data" />
    <Clocks/>
    <Calendar/>
    <Summary/>
  </Layout>
</template>

<style scoped>

</style>
