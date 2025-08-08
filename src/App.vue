<script setup>
  import { ref } from 'vue';
  import Layout from './components/layouts/Layout.vue';
  import Hero from './components/Hero.vue';
  import Clocks from './components/Clocks.vue';
  import Calendar from './components/Calendar.vue'
  import Summary from './components/Summary.vue';

  import {calculateTimeLeft} from './utils'

  const defaultBD = '1991-07-18'
  const defaultLE = 80

  const birthDate = ref(defaultBD)
  const lifeExpectancy = ref(defaultLE)
  const name = ref('Alberto')
  const data = ref(calculateTimeLeft(defaultBD, defaultLE))

  const showModal = ref(false)
  function handleToggleModal() {
    showModal.value = !showModal.value
  }

  function handleUpdateData(n, b, e) {
    if (!n || !b || !r) {return}

    // Salva i nuovi dati nel localstorage del browser

    name.value = n
    birthDate. value = b
    lifeExpectancy.value = parseInt(e)
    data = calculateTimeLeft(b, parseInt(e))
    showModal.value = false
  }

  // Si possono passare i props anche impacchettati in un oggetto tramite v-bind.
  const totalProps = {
    birthDate,
    lifeExpectancy,
    name,
    data
  }

</script>

<template>
  <Layout>
    <Hero :name="name" :data="data" />
    <!--Il v-bind si passa senza i due punti davanti, in quanto ci aspettiamo già un pacchetto con i props!-->
    <Clocks v-bind="totalProps"/>
    <Calendar v-bind="totalProps"/>
    <Summary/>
  </Layout>
</template>

<style scoped>

</style>