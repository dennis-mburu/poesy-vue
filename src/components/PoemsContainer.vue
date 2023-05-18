<template>
  <div class="poems-container">
    <div v-for="poem in poems" :key="poem.id">
      <Poem :poem="poem" @delete-poem="$emit('delete-poem', poem.id)" />
      <!-- <Poem :poem="poem" @delete-poem="handleDelete"/> -->
    </div>
    <!-- {{ console.log(id) }} -->
  </div>
</template>

<script>
import Poem from "./Poem.vue";

export default {
  props: {
    poems: Array,
  },
  components: { Poem },
  methods: {
    // This method works too in combination with line 5
    // handleDelete(id){
    //   this.$emit('delete-poem', id)
    // }
  },
};
</script>

<style scoped>
.poems-container {
  max-width: 30em;
  margin: auto;
}
</style>
