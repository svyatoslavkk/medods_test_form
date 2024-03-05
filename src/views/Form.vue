<script lang="ts">
import { reactive, computed } from "vue";
import { required, minLength } from "@vuelidate/validators";
import useVuelidate from "@vuelidate/core"
import type { FormData } from "@/types/types";

const formData: FormData = reactive({
  lastName: "",
  firstName: "",
  middleName: "",
  dateBirth: "",
  phoneNumber: "",
  gender: "",
  clients: [],
  doctor: "",
  sms: false,
  postalCode: "",
  country: "",
  region: "",
  city: "",
  street: "",
  house: "",
  documentType: "",
  series: "",
  number: "",
  issuedBy: "",
  issueDate: "",
})

const rules = {
  lastName: { required },
  firstName: { required },
  middleName: { required },
  dateBirth: { required },
  phoneNumber: { required },
  gender: { required },
  clients: { required },
  doctor: { required },
  postalCode: { required },
  country: { required },
  region: { required },
  city: { required },
  street: { required },
  house: { required },
  documentType: { required },
  series: { required },
  number: { required },
  issuedBy: { required },
  issueDate: { required },
}

const v$ = useVuelidate(rules, formData);

const submitForm = async () => {
  const result = await v$.value.$validate();
  if (result) {
    alert("Форма заполнена!")
  } else {
    alert("Пожалуйста, заполните все поля")
  }
}

export default {
  data() {
    return {
      currentStep: 0,
      steps: ['StepOne', 'StepTwo', 'StepThree'],
      formData,
      submitForm,
      v$,
      isNextStepClicked: false,
    };
  },
  validations: {
  },
  methods: {
    nextStep() {
      if (this.currentStep < this.steps.length - 1 && !this.v$.$dirty) {
        this.currentStep++;
      }
    },
    prevStep() {
      if (this.currentStep > 0) {
        this.currentStep--;
      }
    },
  }
};
</script>

<template>
  <div id="multistep-form">
    <form class="form-container">
      <fieldset v-if="currentStep === 0">
        <legend>Шаг 1: Личная информация</legend>

        <div class="flex-content">
          <div>
            <span class="input-span">
              <label for="last-name" class="label">Фамилия</label>
              <input type="text" name="last-name" id="last-name" v-model="formData.lastName">
            </span>
            <span class="error-message" v-for="error in v$.lastName.$errors" :key="error.$uid">Обязательно для заполнения</span>
          </div>

          <div>
            <span class="input-span">
              <label for="first-name" class="label">Имя</label>
              <input type="text" name="first-name" id="first-name" v-model="formData.firstName">
            </span>
            <span class="error-message" v-for="error in v$.lastName.$errors" :key="error.$uid">Обязательно для заполнения</span>
          </div>

          <div>
            <span class="input-span">
              <label for="middle-name" class="label">Отчество</label>
              <input type="text" name="middle-name" id="middle-name" v-model="formData.middleName">
            </span>
            <span class="error-message" v-for="error in v$.lastName.$errors" :key="error.$uid">Обязательно для заполнения</span>
          </div>
        </div>

        <span class="input-span">
          <label for="date-birth" class="label">Дата рождения</label>
          <input type="date" name="date-birth" id="date-birth" v-model="formData.dateBirth">
        </span>
        <span class="error-message" v-for="error in v$.lastName.$errors" :key="error.$uid">Обязательно для заполнения</span>

        <span class="input-span">
          <label for="phone-number" class="label">Номер телефона</label>
          <input type="tel" name="phone-number" id="phone-number" v-model="formData.phoneNumber">
        </span>
        <span class="error-message" v-for="error in v$.lastName.$errors" :key="error.$uid">Обязательно для заполнения</span>

        <span class="input-span">
          <label for="gender" class="label">Пол</label>
          <select id="gender" name="gender" v-model="formData.gender">
            <option value="male">Мужской</option>
            <option value="female">Женский</option>
          </select>
        </span>
        <span class="error-message" v-for="error in v$.lastName.$errors" :key="error.$uid">Обязательно для заполнения</span>

        <span class="input-span">
          <label for="client-group" class="label">Группа клиентов</label>
          <select id="client-group" name="client-group" v-model="formData.clients" multiple>
            <option value="VIP">VIP</option>
            <option value="Проблемные">Проблемные</option>
            <option value="ОМС">ОМС</option>
          </select>
        </span>
        <span class="error-message" v-for="error in v$.lastName.$errors" :key="error.$uid">Обязательно для заполнения</span>

        <span class="input-span">
          <label for="attending-doctor" class="label">Лечащий врач</label>
          <select id="attending-doctor" name="attending-doctor" v-model="formData.doctor">
            <option value="Иванов">Иванов</option>
            <option value="Захаров">Захаров</option>
            <option value="Чернышева">Чернышева</option>
          </select>
        </span>
        <span class="error-message" v-for="error in v$.lastName.$errors" :key="error.$uid">Обязательно для заполнения</span>
        
        <span class="input-span">
          <div class="flex-content">
            <label>
              <input type="checkbox" id="no-sms" name="no-sms" v-model="formData.sms">
            </label>
            <label for="no-sms" class="label">Не отправлять СМС</label>
          </div>
        </span>
      </fieldset>
      
      <fieldset v-if="currentStep === 1">
        <legend>Шаг 2: Адрес</legend>

        <span class="input-span">
          <label for="postalCode" class="label">Индекс</label>
          <input type="text" name="postalCode" id="postalCode" v-model="formData.postalCode">
        </span>
        <span class="error-message" v-for="error in v$.lastName.$errors" :key="error.$uid">Обязательно для заполнения</span>

        <span class="input-span">
          <label for="country" class="label">Страна</label>
          <input type="text" name="country" id="country" v-model="formData.country">
        </span>
        <span class="error-message" v-for="error in v$.lastName.$errors" :key="error.$uid">Обязательно для заполнения</span>

        <span class="input-span">
          <label for="region" class="label">Область</label>
          <input type="text" name="region" id="region" v-model="formData.region">
        </span>
        <span class="error-message" v-for="error in v$.lastName.$errors" :key="error.$uid">Обязательно для заполнения</span>

        <span class="input-span">
          <label for="city" class="label">Город</label>
          <input type="text" name="city" id="city" v-model="formData.city">
        </span>
        <span class="error-message" v-for="error in v$.lastName.$errors" :key="error.$uid">Обязательно для заполнения</span>

        <span class="input-span">
          <label for="street" class="label">Улица</label>
          <input type="text" name="street" id="street" v-model="formData.street">
        </span>
        <span class="error-message" v-for="error in v$.lastName.$errors" :key="error.$uid">Обязательно для заполнения</span>

        <span class="input-span">
          <label for="house" class="label">Дом</label>
          <input type="text" name="house" id="house" v-model="formData.house">
        </span>
        <span class="error-message" v-for="error in v$.lastName.$errors" :key="error.$uid">Обязательно для заполнения</span>
      </fieldset>
      
      <fieldset v-if="currentStep === 2">
        <legend>Шаг 3: Паспорт</legend>

        <div class="input-span">
          <label for="documentType" class="label">Тип документа</label>
          <select id="documentType" name="documentType" v-model="formData.documentType" required>
            <option value="">Выберите тип документа</option>
            <option value="Паспорт">Паспорт</option>
            <option value="Свидетельство о рождении">Свидетельство о рождении</option>
            <option value="Вод. удостоверение">Вод. удостоверение</option>
          </select>
        </div>
        <span class="error-message" v-for="error in v$.lastName.$errors" :key="error.$uid">Обязательно для заполнения</span>

        <span class="input-span">
          <label for="series" class="label">Серия</label>
          <input type="text" name="series" id="series" v-model="formData.series" required>
        </span>
        <span class="error-message" v-for="error in v$.lastName.$errors" :key="error.$uid">Обязательно для заполнения</span>

        <span class="input-span">
          <label for="number" class="label">Номер</label>
          <input type="text" name="number" id="number" v-model="formData.number">
        </span>
        <span class="error-message" v-for="error in v$.lastName.$errors" :key="error.$uid">Обязательно для заполнения</span>

        <span class="input-span">
          <label for="issuedBy" class="label">Кем выдан</label>
          <input type="text" name="issuedBy" id="issuedBy" v-model="formData.issuedBy">
        </span>
        <span class="error-message" v-for="error in v$.lastName.$errors" :key="error.$uid">Обязательно для заполнения</span>

        <span class="input-span">
          <label for="issueDate" class="label">Дата выдачи</label>
          <input type="date" name="issueDate" id="issueDate" v-model="formData.issueDate">
        </span>
        <span class="error-message" v-for="error in v$.lastName.$errors" :key="error.$uid">Обязательно для заполнения</span>

      </fieldset>

      <div class="flex-content">
        <input v-if="currentStep > 0" type="button" class="prev-button" @click="prevStep" :data-step="currentStep" value="Назад" />
        <input v-if="currentStep < steps.length - 1" type="button" class="next-button" @click="nextStep" :data-step="currentStep" value="Далее" />
        <input v-else type="submit" @click="submitForm" class="next-button" :data-step="currentStep" value="Отправить" />
      </div>
    </form>
  </div>
</template>

<style>
.form-container {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  background-color: #525050;
  border: 2px solid #6c6868;
  border-radius: 5px;
  padding: 20px;
  width: 100%;
  margin: 0 auto;
}

.flex-content {
  display: flex;
  gap: 0.5rem;
  align-items: center;
  justify-content: center;
}

fieldset {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  border: 2px solid #6c6868;
}

legend {
  font-weight: 600;
  font-size: 18px;
  color: #ddd;
}

.label {
  align-self: flex-start;
  color: #58bc82;
  font-weight: 600;
}

input,
select,
input[type="button"],
input[type="submit"] {
  border-radius: 0.5rem;
  padding: 0.5rem 0.33rem;
  width: 100%;
  border: none;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  background-color: #efefef;
  border: 2px solid #6c6868;
}

input[type="button"],
input[type="submit"] {
  font-weight: 600;
  justify-content: center;
}

input[type="button"]:hover,
input[type="submit"]:hover {
  background-color: #d8d5d5;
}

.error-message {
  font-size: 13px;
  font-weight: 500;
  color: #fe7575;
}

@media (min-width: 1024px) {
  fieldset {
    min-width: 400px;
  }
}
</style>