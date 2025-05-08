<script setup>
import { defineProps, defineEmits, ref, watch } from 'vue';

const props = defineProps({
    modelValue: {
        type: String,
        default: 'soma',
    },
});

const emit = defineEmits(['update:modelValue']);
const selectedOperation = ref(props.modelValue);

watch(() => props.modelValue, (newValue) => {
    selectedOperation.value = newValue;
});

watch(selectedOperation, (newValue) => {
    emit('update:modelValue', newValue);
});
</script>

<template>
    <p class="text-end mt-4 d-flex align-items-center">
        <span class="fw-bold me-2">Selecione a operação desejada:</span>
        <select class="form-select w-auto" v-model="selectedOperation" @change="$emit('update:modelValue', selectedOperation)">
            <option value="soma">Somar +</option>
            <option value="subtrair">Subtrair -</option>
            <option value="multiplicar">Multiplicar *</option>
            <option value="dividir">Dividir /</option>
        </select>
    </p>
</template>
