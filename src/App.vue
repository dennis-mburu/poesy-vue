<template>
  <div class="app">
    <div class="sidebar">
      <button @click="this.showPoemForm = !this.showPoemForm">
        Show/hide new poem form
      </button>
      <NewPoemForm v-show="showPoemForm" @add-newPoem="addNewPoem" />
    </div>
    <PoemsContainer :poems="poems" @delete-poem="handlePoemDelete" />
  </div>
</template>

<script>
import PoemsContainer from "./components/PoemsContainer.vue";
import NewPoemForm from "./components/NewPoemForm.vue";

export default {
  components: {
    PoemsContainer,
    NewPoemForm,
  },
  data() {
    return {
      poems: [],
      showPoemForm: false,
    };
  },
  methods: {
    addNewPoem(newPoem) {
      this.poems = [...this.poems, newPoem];
    },

    handlePoemDelete(id) {
      this.poems = this.poems.filter((poem) => poem.id !== id);
    },

    // async fetchPoems() {
    //   const res = await fetch(`http://localhost:3002/poems`);
    //   const data = await res.json();
    //   return data;
    // },
    
  },

  // async created() {
  //   this.poems = await this.fetchPoems();
  // },
  created() {
    fetch("http://localhost:3002/poems")
      .then((res) => res.json())
      .then((data) => (this.poems = data));
  },
};
</script>

<style scoped>
.app {
  display: flex;
  flex-direction: row;
}

.sidebar {
  background: #e5fdff;
  min-height: 100vh;
  min-width: 12em;
  width: 28%;
  padding: 1em;
  border-right: solid black 1px;
}

button {
  width: 100%;
}
</style>
