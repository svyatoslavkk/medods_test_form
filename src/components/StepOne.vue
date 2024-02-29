<script lang="ts">
export default {
  data() {
    return {
      lastName: '',
      firstName: '',
      middleName: '',
      dateBirth: '',
      phoneNumber: '',
      gender: '',
      clients: [],
      doctor: '',
    };
  }
};
</script>

<template>
  <fieldset>
    <legend>Шаг 1: Личная информация</legend>

    <span class="input-span">
      <label for="last-name" class="label">Фамилия</label>
      <input type="text" name="last-name" id="last-name">
    </span>

    <span class="input-span">
      <label for="first-name" class="label">Имя</label>
      <input type="text" name="first-name" id="first-name">
    </span>

    <span class="input-span">
      <label for="middle-name" class="label">Отчество</label>
      <input type="text" name="middle-name" id="middle-name">
    </span>

    <span class="input-span">
      <label for="middle-name" class="label">Дата рождения</label>
      <input type="date" name="middle-name" id="middle-name">
    </span>

    <span class="input-span">
      <label for="phone-number" class="label">Номер телефона</label>
      <input type="tel" name="phone-number" id="phone-number">
    </span>

    <span class="input-span">
      <label for="gender" class="label">Пол</label>
      <select id="gender" name="gender">
        <option value="male">Мужской</option>
        <option value="female">Женский</option>
      </select>
    </span>

    <span class="input-span">
      <label for="client-group" class="label">Группа клиентов</label>
      <select id="client-group" name="client-group" multiple>
        <option value="VIP">VIP</option>
        <option value="Проблемные">Проблемные</option>
        <option value="ОМС">ОМС</option>
      </select>
    </span>

    <span class="input-span">
      <label for="attending-doctor" class="label">Лечащий врач</label>
      <select id="attending-doctor" name="attending-doctor" >
        <option value="Иванов">Иванов</option>
        <option value="Захаров">Захаров</option>
        <option value="Чернышева">Чернышева</option>
      </select>
    </span>
        
    <span class="input-span">
      <div class="flex-content">
        <label>
          <input type="checkbox" id="no-sms" name="no-sms">
        </label>
        <label for="no-sms" class="label">Не отправлять СМС</label>
      </div>
    </span>
  </fieldset>
</template>

<style>

</style>