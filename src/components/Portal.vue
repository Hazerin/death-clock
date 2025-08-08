<script setup>
import { Teleport } from 'vue';

  defineProps({
    showModal: Boolean,
    handleCloseModal: Function
  })
</script>

<template>
    <Teleport to="#portal">

    </Teleport>
</template>

<style scoped>

</style>
