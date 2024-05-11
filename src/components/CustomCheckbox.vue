<script setup>
    const emit = defineEmits(['update:modelValue']);
    const props = defineProps({
        modelValue: {
            type: Boolean,
            default: false,
        },

        label: {
            type: String,
            default: '',
        },
    });
    const handleChange = (ev) => {
        emit('update:modelValue', ev.target.checked);
    };
</script>
<template>
    <input
        type="checkbox"
        :checked="modelValue"
        @change="handleChange"
        class="border-[1px] border-gray-300" />
    <label v-if="label">{{ label }}</label>
</template>