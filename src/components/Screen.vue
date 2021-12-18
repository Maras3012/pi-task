<template>
  <div class="grid md:grid-cols-3 gap-10">

    <div class="shadow-md bg-red-500 p-10 text-center rounded-3xl">
      <h3 class="text-3xl text-black font-bold mb-4">Cases</h3>

      <div class="text-2xl mb-4">
        <span class="font-bold">New:</span>
        {{ stats.NewConfirmed.toLocaleString() }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">Total:</span>
        {{ stats.TotalConfirmed.toLocaleString() }}
      </div>
    </div>

    <div class="shadow-md bg-gray-500 p-10 text-center rounded-3xl">
      <h3 class="text-3xl text-black font-bold mb-4">Deaths</h3>

      <div class="text-2xl mb-4">
        <span class="font-bold">New:</span>
        {{ stats.NewDeaths.toLocaleString() }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">Total:</span>
        {{ stats.TotalDeaths.toLocaleString() }}
      </div>
    </div>
    
    <div class="shadow-md bg-green-500 p-10 text-center rounded-3xl">
      <h3 class="text-3xl text-black font-bold mb-4">Recovered</h3>

      <div class="text-2xl mb-4">
        <span class="font-bold">New:</span>
        {{ stats.NewRecovered.toLocaleString() }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">Total:</span>
        {{ stats.TotalRecovered.toLocaleString() }}
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'Screen',
  props: ['stats'],
};
</script>
