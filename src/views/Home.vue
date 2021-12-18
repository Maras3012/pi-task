<template>
  <main v-if="!loading">
    <Title :dataDate="dataDate" :text="title" />

    <Countries :countries="countries" @get-country="getCountry" />

    <button
      v-if="status.Country"
      class="bg-black text-white rounded p-3 mt-10 ml-10 focus:outline-none hover:bg-gray-600"
      @click="clearCountry"
    >World</button>
    
    <Screen :stats="status" />
  </main>

  <main v-else class="flex flex-col align-center justify-center text-center">
    <div class="text-gray-500 text-3xl mt-10 mb-6">
      Loading
    </div>
    <img :src="require('../assets/loading.gif')" alt="..." class="w-24 m-auto" />
  </main>
</template>

<script>
import Countries from '@/components/Countries';
import Screen from '@/components/Screen';
import Title from '@/components/Title';
import { ref } from 'vue';

export default {
  name: 'Home',
  components: {
    Title,
    Screen,
    Countries
  },
  setup () {
    const loading = ref(true);
    const title = ref('World');
    const dataDate = ref('');
    const status = ref({});
    const countries = ref([]);

    const fetchData = async () => {
      try {
        const res = await fetch('https://api.covid19api.com/summary')
        return await res.json();
      } catch(e) {
        console.log(e, 'Error fetching data');
      }
    };

    const getCountry = (country) => {
      try {
        status.value = country;
        title.value = country.Country;
      } catch(e){
        console.log(e, 'Error getting country data');
      }
    };

    const clearCountry = async () => {
      try {
        loading.value = true;
        const data = await fetchData();
        title.value = 'World';
        status.value = data.Global;
        loading.value = false;
      } catch(e){
        console.log(e, 'Error clearing country');
      }
      
    };

    const baseSetup = async () => {
      try {
        const data = await fetchData();

        dataDate.value = data.Date;
        status.value = data.Global;
        countries.value = data.Countries;
        loading.value = false;
      } catch(e){
        console.log(e, 'Error setting default data');
      }
    };

    baseSetup();

    return {
      loading,
      title,
      dataDate,
      status,
      countries,
      getCountry,
      clearCountry
    };
  }
};
</script>
