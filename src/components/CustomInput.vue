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
    const handleLabelClick = (ev) => {
        const label = ev.target;
        const input = label.nextElementSibling;
        input.focus();
    };

</script>
<template>
    <div class="inline-block">
        <label @click="handleLabelClick">{{ label }}</label>
        <input
            v-bind="attrs"
            :placeholder="label"
            :value="modelValue"
            class="px-3 py-2 rounded border-[1px] border-gray-300 focus:outline-none focus:border-2 focus:border-blue-500"
            @input="(ev) => emit('update:modelValue', ev.target.value)">
    </div>
</template>