<script lang="ts">
export default {
  data() {
    return {
      formSteps: [
        {
          title: "Шаг 1: Личная информация",
          fields: [
            { id: "last-name", label: "Фамилия", type: "text", required: true },
            { id: "first-name", label: "Имя", type: "text", required: true },
            {
              id: "middle-name",
              label: "Отчество",
              type: "text",
              required: true,
            },
            {
              id: "birthdate",
              label: "Дата рождения",
              type: "date",
              required: true,
            },
            {
              id: "phone-number",
              label: "Номер телефона",
              type: "tel",
              required: true,
            },
          ],
        },
        {
          title: "Шаг 2: Контактная информация",
          fields: [
            { id: "email", label: "Email", type: "email", required: true },
            { id: "phone", label: "Телефон", type: "tel", required: true },
          ],
        },
        {
          title: "Шаг 3: Пароль",
          fields: [
            {
              id: "password",
              label: "Пароль",
              type: "password",
              required: true,
            },
            {
              id: "confirm-password",
              label: "Подтвердите пароль",
              type: "password",
              required: true,
            },
          ],
        },
      ],
      formData: {
        "first-name": "",
        "last-name": "",
        email: "",
        phone: "",
        password: "",
        "confirm-password": "",
      },
      currentStep: 0,
    };
  },
  methods: {
    nextStep() {
      if (this.currentStep < this.formSteps.length - 1) {
        this.currentStep++;
      }
    },
    prevStep() {
      if (this.currentStep > 0) {
        this.currentStep--;
      }
    },
    submitForm() {
      // Ваша логика отправки данных формы
    },
  },
};
</script>

<template>
  <form @submit.prevent="submitForm" id="multistep-form" class="form-container">
    <fieldset
      v-for="(step, index) in formSteps"
      :key="index"
      v-show="currentStep === index"
    >
      <h3>{{ step.title }}</h3>
      <div v-for="field in step.fields" :key="field.id">
        <label :for="field.id">{{ field.label }}:</label>
        <input
          :type="field.type"
          :id="field.id"
          :name="field.id"
          v-model="formData[field.id]"
          :required="field.required"
        />
      </div>
    </fieldset>
    <div class="flex-content">
      <input
        v-if="currentStep > 0"
        type="button"
        class="prev-button"
        @click="prevStep"
        :data-step="currentStep"
        value="Назад"
      />
      <input
        v-if="currentStep < formSteps.length - 1"
        type="button"
        class="next-button"
        @click="nextStep"
        :data-step="currentStep"
        value="Далее"
      />
      <input
        v-else
        type="submit"
        class="next-button"
        :data-step="currentStep"
        value="Отправить"
      />
    </div>
  </form>
</template>

<style>

</style>
