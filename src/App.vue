<script lang="ts">
import Form from "./views/Form.vue";
export default {
  components: {
    Form,
  },
};
</script>

<template>
  <div id="app">
    <form class="container">
      <Form />
    </form>

    <router-view />
  </div>
</template>

<style scoped>
.container {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100vh;
  background-color: #343333;
  margin: 0 auto;
}
</style>
