<script>
export default{
    props: {
      user: {
        type: Object,
        required: true
      },
    },

    /* opposite of props. child sends data to parent */
    emits: ['change-name']
};
</script>

<template>
    <h1>User: {{ user.name }}</h1>
    <p>Favorite Food: {{ user.food }}</p>
    <button @click="$emit('change-name')">Change Name</button>
</template>
