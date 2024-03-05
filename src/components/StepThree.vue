<script lang="ts">
import { reactive } from "vue";
import { required } from "@vuelidate/validators";

const formData = reactive({
  documentType: "",
  series: "",
  number: "",
  issuedBy: "",
  issueDate: "",
});

const rules = {
  documentType: { required },
  series: { required },
  number: { required },
  issuedBy: { required },
  issueDate: { required },
};
</script>

<template>
  <fieldset>
    <legend>Шаг 3: Паспорт</legend>

    <div>
      <label for="documentType" class="label">Тип документа</label>
      <select id="documentType" name="documentType" required>
        <option value="">Выберите тип документа</option>
        <option value="Паспорт">Паспорт</option>
        <option value="Свидетельство о рождении">
          Свидетельство о рождении
        </option>
        <option value="Вод. удостоверение">Вод. удостоверение</option>
      </select>
    </div>

    <span class="input-span">
      <label for="series" class="label">Серия</label>
      <input type="text" name="series" id="series" />
    </span>

    <span class="input-span">
      <label for="number" class="label">Номер</label>
      <input type="text" name="number" id="number" />
    </span>

    <span class="input-span">
      <label for="issuedBy" class="label">Кем выдан</label>
      <input type="text" name="issuedBy" id="issuedBy" />
    </span>

    <span class="input-span">
      <label for="issueDate" class="label">Дата выдачи</label>
      <input type="text" name="issueDate" id="issueDate" />
    </span>
  </fieldset>
</template>

<style></style>
