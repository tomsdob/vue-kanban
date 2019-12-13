<template>
    <Tasks />
</template>

<script>
import "./assets/tailwind.css";

import Tasks from "./components/Tasks.vue";

export default {
  name: 'app',
  components: {
    Tasks
  }
}
</script>

<style>
html, body{
  margin: 0;
  padding: 0;
}
</style>
