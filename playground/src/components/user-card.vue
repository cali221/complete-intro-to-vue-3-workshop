<script>
import {useCount} from '../composables/countStore.js'

export default{
    setup(){
      const countStore = useCount();
      return{
       countStore
      }
    },
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
    <h2>New Counter</h2>
    <p>Global Count: {{ countStore.globalCount }}</p>
    <p>Local Count: {{ countStore.localCount }}</p>
    <button @click="countStore.incrementGlobalCount">Global</button>
    <button @click="countStore.increcmentLocalCount">Local</button>
    <hr />
    <p>Favorite Food: {{ user.food }}</p>
    <button @click="$emit('change-name')">Change Name</button>
</template>
