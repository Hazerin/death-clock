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
        <div class="btns-container">
            <button>
                Not {{ name }}?
            </button>
            <button class="link-button">
                Copy link
            </button>
            <button class="link-button">
                Reset data
            </button>
        </div>
        <div class="progress-bar">
            <div>
                <div>
                    <i class="fa-solid fa-baby"></i>
                    <h6 class="bar-label">Birth</h6>
                </div>
                <h6>
                    {{ 45 }}%
                </h6>
            </div>
            <div>
                <h6 class="bar-label">Death</h6>
                <i class="fa-solid fa-skull"></i>
            </div>
        </div>
    </section>
</template>

<style scoped>

</style>
