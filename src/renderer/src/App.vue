<script setup>
import { onMounted, ref } from 'vue';
import { eleringAPI } from '../../../api/elering_api';

const prices = ref();

onMounted(async () => {
    try {
        prices.value = await eleringAPI.get('/balance/total/latest');
        console.log(prices.value)
    } catch(error) {
        throw new Error(error)
    }
})
</script>

<template>
</template>

<style lang="less">
@import './assets/css/styles.less';
</style>
