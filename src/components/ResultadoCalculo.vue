<template>
    <p class="text-start mt-3"><b>Resultado:</b> {{ resultado }} </p>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    resultado: {
        type: [Number, String],
        default: 0,
    },
});
</script>