<script setup>
const props = defineProps({
  modelValue: { type: String, required: true },
  placeholder: { type: String, default: 'Rechercher…' }
})
const emit = defineEmits(['update:modelValue'])
</script>

<template>
  <input
    class="search"
    :placeholder="placeholder"
    :value="modelValue"
    @input="emit('update:modelValue', $event.target.value)"
    type="text"
  />
</template>

<style scoped>
.search {
  flex: 1 1 280px;
  padding: 10px 12px;
  border: 1px solid #ddd;
  border-radius: 8px;
  outline: none;
}
.search:focus { 
  border-color: #42b983; 
}
</style>
