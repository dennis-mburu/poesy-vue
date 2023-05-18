<template>
  <div>
    <h3>{{ poem.title }}</h3>
    <p>{{ poem.content }}</p>
    <p>
      <strong>- By {{ poem.author }}</strong>
    </p>
    <button>Mark as {{ poem.readstatus ? "unread" : "read" }}</button>
    <button @click="handleDelete(poem.id)" style="float: right">
      Delete Poem
    </button>
  </div>
</template>

<script>
export default {
  props: ["poem"],
  methods: {
    async handleDelete(id) {
      // this can work too without passing the poem.id on
      // the click event, just leaving it as handleDelete
      // console.log(this.poem.id)

      //   fetch(`http://localhost:3002/poems/${id}`, {
      //     method: "DELETE",
      //   })
      //     .then((res) => {
      //       //   console.log(res);
      //   res.ok
      //     ? this.$emit("delete-poem", id)
      //     : alert("Error: " + res.statusText);
      //     })
      //     .catch((err) => {
      //       alert(err);
      //     });

      // Trying async await syntax

      try {
        const res = await fetch(`http://localhost:3002/poems/${id}`, {
          method: "DELETE",
        });
        res.ok
          ? this.$emit("delete-poem", id)
          : alert("Error: " + res.statusText);
      } catch (error) {
        alert(error);
      }
    },
  },
};
</script>
