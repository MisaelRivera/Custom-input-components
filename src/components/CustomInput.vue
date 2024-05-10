<script setup>
    import { getCurrentInstance } from 'vue';
    const { attrs } = getCurrentInstance();
    const props = defineProps({
        label: {
            type: String,
            default: '',
        },

        modelValue: {
            type: [String, Number],
            default: '',
        }
    });
    const emit = defineEmits(['update:modelValue']);
</script>
<template>
    <label>{{ label }}</label>
    <input
        v-bind="attrs"
        :placeholder="label"
        :value="modelValue"
        class="px-3 py-2 rounded border-[1px] border-slate-700 focus:outline-none focus:border-2 focus:border-blue-500"
        @input="(ev) => emit('update:modelValue', ev.target.value)">
</template>