<script setup>
import { Teleport } from 'vue';

  defineProps({
    showModal: Boolean,
    handleCloseModal: Function
  })
</script>

<template>
    <Teleport to="#portal" v-if="showModal">
      <div class="portal-container">
        <!--role e tabindex servono ad attribuire a un div le caratteristiche di un button-->
        <div class="portal-underlay" role="button" tabindex="0"
        @click="handleCloseModal"
        @keydown.esc="handleCloseModal"></div>
        <div class="portal-content">
          <slot/>
        </div>
      </div>
    </Teleport>
</template>

<style scoped>

</style>