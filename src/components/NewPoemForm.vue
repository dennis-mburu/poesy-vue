<template>
  <form class="new-poem-form" @submit="handleSubmit">
    <input type="text" name="title" placeholder="Title" v-model="title" />
    <input type="text" name="author" placeholder="Author" v-model="author" />
    <textarea
      name="content"
      rows="10"
      v-model="content"
      placeholder="Share your masterpiece here..."
    ></textarea>
    <input type="submit" value="Share your masterpiece" />
  </form>
  <!-- {{ console.log(this) }} -->
</template>

<script>
export default {
  data() {
    return {
      title: "",
      author: "",
      content: "",
    };
  },
  methods: {
    async handleSubmit(e) {
      e.preventDefault();

      const newPoem = {
        title: this.title,
        author: this.author,
        content: this.content,
      };

      // fetch('http://localhost:3002/poems', {
      //   method: 'POST',
      //   headers: {
      //     'Content-Type': 'application/json'
      //   },
      //   body: JSON.stringify(newPoem)
      // })
      // .then(res => res.json())
      // .then(data => this.$emit('add-newPoem', data))

      // Trying async await syntax
      try {
        const res = await fetch("http://localhost:3002/poems", {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify(newPoem),
        });
        // console.log(res)
        const poem = await res.json();
        this.$emit("add-newPoem", poem);
        (this.title = ""), (this.author = ""), (this.content = "");
      } catch (error) {
        // console.log(error);
        alert(error);
      }
    },
  },
};
</script>

<style scoped>
.new-poem-form {
  border: 1px solid;
  padding: 1em;
  display: flex;
  flex-direction: column;
}

input,
textarea {
  font-size: 1em;
  font-family: sans-serif;
  margin-bottom: 0.5em;
}
</style>
