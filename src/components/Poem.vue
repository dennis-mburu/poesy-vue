<template>
    <div>
        <h3>{{ poem.title }}</h3>
        <p>{{ poem.content }}</p>
        <p><strong>- By {{ poem.author }}</strong></p>
        <button>Mark as {{ poem.readstatus ? "unread" : "read" }}</button>
        <button style="float: right;"> Delete Poem</button>
    </div>
</template>

<script>
    export default {
        props: ['poem']
    }
</script>