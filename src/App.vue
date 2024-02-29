<script lang="ts">
import Form from './views/Form.vue';
import TestForm from './views/TestForm.vue';
import StepOne from './components/StepOne.vue';
import StepTwo from './components/StepTwo.vue';
import StepThree from './components/StepThree.vue';
export default {
  components: {
    StepOne,
    StepTwo,
    StepThree,
    Form,
    TestForm,
  },
  data() {
    return {
      currentStep: 0
    };
  },
  methods: {
    nextStep() {
    },
    prevStep() {
    },
    submitForm() {
      // Ваша логика отправки данных формы
    }
  }
};
</script>

<template>
  <div id="app">
    <form class="container">
      <!-- <StepOne />
      <StepTwo />
      <StepThree /> -->
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
