<script lang="ts">
  import StepOne from '@/components/StepOne.vue';
  import StepTwo from '@/components/StepTwo.vue';
  import StepThree from '@/components/StepThree.vue';

  export default {
  components: {
    StepOne,
    StepTwo,
    StepThree
  },
  data() {
    return {
      currentStep: 0,
      steps: ['StepOne', 'StepTwo', 'StepThree']
    };
  },
  computed: {
    currentStepComponent() {
      return this.steps[this.currentStep];
    }
  },
  methods: {
    nextStep() {
      if (this.currentStep < this.steps.length - 1) {
        this.currentStep++;
      }
    },
    prevStep() {
      if (this.currentStep > 0) {
        this.currentStep--;
      }
    },
    submitForm() {
      // Логика отправки формы
    }
  }
};
</script>

<template>
  <div id="multistep-form">
    <form @submit.prevent="submitForm" class="form-container">
      <component :is="currentStepComponent" />
      <div class="flex-content">
        <input v-if="currentStep > 0" type="button" class="prev-button" @click="prevStep" :data-step="currentStep" value="Назад" />
        <input v-if="currentStep < steps.length - 1" type="button" class="next-button" @click="nextStep" :data-step="currentStep" value="Далее" />
        <input v-else type="submit" class="next-button" :data-step="currentStep" value="Отправить" />
      </div>
    </form>
  </div>
</template>

<style>
</style>