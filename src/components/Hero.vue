<script setup>
  const {name , data} = defineProps({
    name: String,
    data: Object
  })
</script>

<template>
    <section id="hero">
        <h3 class="text-large">
            <!--Oltre che col punto, si può accedere al dato con la corrispondente stringa usata come chiave-->
            {{ name }}, you have {{ data["weeks"] }} weeks left. Make them count😄
        </h3>
    </section>
</template>

<style scoped>

</style>
