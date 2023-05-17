<template>
  <form class="new-poem-form">
    <input type="text" name="title" placeholder="Title" />
    <input type="text" name="author" placeholder="Author" />
    <textarea
      name="content"
      rows="10"
      placeholder="Share your masterpiece here..."
    ></textarea>
    <input type="submit" value="Share your masterpiece" />
  </form>
</template>

<script>
export default {};
</script>

<style scoped>
    .new-poem-form {
        border: 1px solid ;
        padding: 1em;
        display: flex;
        flex-direction: column;
    }

    input, textarea{
        font-size: 1em;
        font-family: sans-serif;
        margin-bottom: 0.5em;
    }
</style>
