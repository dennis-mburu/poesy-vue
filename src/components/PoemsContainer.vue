<template>
  <div class="poems-container">
    <div v-for="poem in poems" :key="poem.id">
      <Poem :poem="poem" />
    </div>
  </div>
</template>

<script>
import Poem from "./Poem.vue";

export default {
  props: {
    poems: Array,
  },
  components: { Poem },
};
</script>

<style scoped>
.poems-container {
  max-width: 30em;
  margin: auto;
}
</style>
