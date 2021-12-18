<template>
  <select
    v-model="selected"
    class="form-select mb-10 inline-block w-100 border p-3 rounded"
    @change="onChange()"
  >
    <option value="0">Countries</option>
    <option v-for="country in countries" :value="country.ID">
      {{ country.Country }}
    </option>
  </select>
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'Countries',
  props: ['countries'],
  setup ({ countries }, { emit }) {
    const selected = ref(0);

    return {
      selected,
      onChange () {
        const country = countries.find((item) => item.ID === selected.value);
        emit('get-country', country);
      }
    };
  }
};
</script>
