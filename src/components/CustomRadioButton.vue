<script setup>
    import { getCurrentInstance } from 'vue';
    const { attrs } = getCurrentInstance();
    const emit = defineEmits(['update:modelValue']);
    const props = defineProps({
        label: {
            type: String,
            default: '',
        },

        modelValue: {
            type: [String, Number],
            default: '',
        },

        value: {
            type: [String, Number],
            required: true,
        },
    });

    const handleChange = () => {
        emit('update:modelValue', props.value);
    };
</script>
<template>
    <div class="inline-block">
        <input 
            type="radio"
            v-bind="attrs"
            :value="value"
            :checked="modelValue === value"
            @change="handleChange">
        <label v-if="label">{{ label }}</label>
    </div>
</template>