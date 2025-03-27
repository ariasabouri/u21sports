<template>
    <div class="form-group">
        <label v-if="label" :for="id">{{ label }}</label>
        <textarea v-if="type === 'textarea'" :id="id" v-model="inputValue" :placeholder="placeholder" :rows="rows"
            :required="required" class="form-input textarea" @input="updateValue"></textarea>
        <select v-else-if="type === 'select'" :id="id" v-model="inputValue" :required="required"
            class="form-input select" @change="updateValue">
            <option v-if="placeholder" value="" disabled selected>{{ placeholder }}</option>
            <option v-for="(option, index) in options" :key="index" :value="option.value">
                {{ option.label }}
            </option>
        </select>
        <input v-else :id="id" :type="type" v-model="inputValue" :placeholder="placeholder" :required="required"
            class="form-input" @input="updateValue">
    </div>
</template>

<script setup lang="ts">
import { ref, watch, onMounted } from 'vue';

interface Option {
    label: string;
    value: string | number;
}

const props = defineProps<{
    modelValue: string | number;
    id?: string;
    label?: string;
    type?: 'text' | 'email' | 'password' | 'number' | 'tel' | 'date' | 'textarea' | 'select';
    placeholder?: string;
    required?: boolean;
    options?: Option[];
    rows?: number;
}>();

const emit = defineEmits<{
    (e: 'update:modelValue', value: string | number): void;
}>();

const inputValue = ref(props.modelValue);

// Watch for external changes to modelValue
watch(() => props.modelValue, (newValue) => {
    inputValue.value = newValue;
});

// Update parent value when input changes
const updateValue = () => {
    emit('update:modelValue', inputValue.value);
};

// Generate random ID if not provided
onMounted(() => {
    if (!props.id) {
        const randomId = `form-input-${Math.random().toString(36).substring(2, 9)}`;
        inputValue.value = randomId;
    }
});
</script>

<style scoped>
.form-group {
    display: flex;
    flex-direction: column;
    gap: 8px;
    margin-bottom: 20px;
    width: 100%;
}

label {
    font-family: "Roboto-SemiBold", Helvetica, sans-serif;
    font-size: 14px;
    color: var(--color-text);
}

.form-input {
    padding: 12px;
    border: 1px solid rgba(255, 255, 255, 0.3);
    border-radius: 8px;
    background-color: var(--color-background);
    color: var(--color-text);
    font-family: "Roboto-Regular", Helvetica, sans-serif;
    font-size: 16px;
    width: 100%;
    transition: all 0.3s ease;
}

.form-input:focus {
    outline: none;
    border-color: var(--color-primary);
    box-shadow: 0 0 0 1px var(--color-primary);
}

.form-input::placeholder {
    color: rgba(255, 255, 255, 0.5);
}

.textarea {
    min-height: 120px;
    resize: vertical;
}

.select {
    appearance: none;
    background-image: url("data:image/svg+xml;charset=UTF-8,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='white'%3e%3cpath d='M7 10l5 5 5-5z'/%3e%3c/svg%3e");
    background-repeat: no-repeat;
    background-position: right 12px center;
    background-size: 20px;
    padding-right: 40px;
}
</style>