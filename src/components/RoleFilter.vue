<script setup>
const props = defineProps({
  modelValue: { type: String, required: true }
})
const emit = defineEmits(['update:modelValue'])

const roles = ['Tous', 'Duelist', 'Initiator', 'Sentinel', 'Controller']
</script>

<template>
  <select
    class="select"
    :value="modelValue"
    @change="emit('update:modelValue', $event.target.value)"
  >
    <option v-for="r in roles" :key="r" :value="r">{{ r }}</option>
  </select>
</template>

<style scoped>
.select {
  padding: 10px 12px;
  border: 1px solid #ddd;
  border-radius: 8px;
}
</style>
