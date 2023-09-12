<script setup>
import { onMounted, ref } from 'vue'

const prices = ref(null);
const test = async () => {
  return await window.api.doSomething('https://dashboard.elering.ee/api/balance/total/latest')
}

onMounted(async () => {
  prices.value = await test()
})
</script>

<template>
  <div class="h-screen w-screen grid grid-cols-2 grid-rows-2 p-6 gap-6">
    <div class="bg-[#fefcfd] rounded p-2">
      <h1 class="text-lg">HINNAD</h1>
      <div class="h-">
        <p v-if="prices">{{ prices.data[0].consumption_local_total }}</p>
      </div>
    </div>
    <div class="bg-[#fefcfd] rounded p-2">
      <h1 class="text-lg">ELEKTER</h1>
    </div>
  </div>
</template>