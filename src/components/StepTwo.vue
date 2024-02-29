<script lang="ts">
export default {
  data() {
    return {
      postalCode: '',
      country: '',
      region: '',
      city: '',
      street: '',
      house: '',
    };
  }
};
</script>

<template>
      <fieldset>
        <legend>Шаг 2: Адрес</legend>

        <span class="input-span">
          <label for="postalCode" class="label">Индекс</label>
          <input type="text" name="postalCode" id="postalCode">
        </span>

        <span class="input-span">
          <label for="country" class="label">Страна</label>
          <input type="text" name="country" id="country">
        </span>

        <span class="input-span">
          <label for="region" class="label">Область</label>
          <input type="text" name="region" id="region">
        </span>

        <span class="input-span">
          <label for="city" class="label">Город</label>
          <input type="text" name="city" id="city">
        </span>

        <span class="input-span">
          <label for="street" class="label">Улица</label>
          <input type="text" name="street" id="street">
        </span>

        <span class="input-span">
          <label for="house" class="label">Дом</label>
          <input type="text" name="house" id="house">
        </span>

      </fieldset>
</template>

<style>

</style>