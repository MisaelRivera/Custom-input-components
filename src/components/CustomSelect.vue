<script setup>
    import { getCurrentInstance } from 'vue';
    const props = defineProps({
        label: {
            type: String,
            default: '',
        },

        modelValue: {
            type: [String, Number, null],
            default: null,
        },

        options: {
            type: Array,
            required: true,
        },
    });

    const emit = defineEmits(['update:modelValue']);
    const { attrs } = getCurrentInstance();
    const handleChange = (ev) => {
        console.log(ev.target.value);
        emit('update:modelValue', ev.target.value);
    };

    const handleLabelClick = (ev) => {
        const label = ev.target;
        const input = label.nextElementSibling;
        input.focus();
    };
</script>
<template>
    <div class="inline-block">
        <label 
            v-if="label"
            @click="handleLabelClick">
            {{ label }}
        </label>
        <select 
            :value="modelValue"
            @change="handleChange"
            v-bind="attrs"
            class="px-2 py-2 border-[1px] border-gray-300 rounded focus:outline-none focus:border-2 focus:border-blue-500">
            <option v-for="option in options"
                :value="option.value"
                :key="option.value"
                :selected="option.value === modelValue">{{ option.label }}</option>
        </select>
    </div>
</template>