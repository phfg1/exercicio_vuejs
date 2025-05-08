<script setup>
import { defineProps, defineEmits, ref, watch } from 'vue';

const props = defineProps({
    placeholder: {
        type: String,
        default: '',
    },
    modelValue: {
        type: Number,
        default: 0,
    },
});

const emit = defineEmits(['update:modelValue']);
const inputValue = ref(props.modelValue);

watch(() => props.modelValue, (newValue) => {
    inputValue.value = newValue;
});

watch(inputValue, (newValue) => {
    emit('update:modelValue', newValue);
});
</script>

<template>
    <p class="mt-4">
        <input type="number" required :placeholder="placeholder" class="form-control" v-model.number="inputValue"
            @input="$emit('update:modelValue', inputValue)">
    </p>
</template>