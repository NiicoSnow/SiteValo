<script setup>
const props = defineProps({
  agents: { type: Array, required: true } // [{id, name, role, difficulty}]
})
const emit = defineEmits(['select'])

function selectAgent(agent) {
  emit('select', agent)
}
</script>

<template>
  <div class="grid">
    <AgentCard
      v-for="agent in agents"
      :key="agent.id"
      :name="agent.name"
      :role="agent.role"
      :difficulty="agent.difficulty"
      @select="selectAgent(agent)"
    />
  </div>
</template>

<script>
import AgentCard from './AgentCard.vue'
export default { components: { AgentCard } }
</script>

<style scoped>
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 12px;
}
</style>
