<script setup>
const props = defineProps({
  agent: {
    type: Object,
    required: true // {id, name, role, difficulty}
  }
})
const emit = defineEmits(['close'])
</script>

<template>
  <div class="overlay" @click.self="emit('close')">
    <div class="panel">
      <header class="panel-header">
        <h2 class="nom-agent">{{ agent.name }}</h2>
        <button class="close" @click="emit('close')">×</button>
      </header>
      <ul class="info">
        <li><strong>Rôle :</strong> {{ agent.role }}</li>
        <li><strong>Difficulté :</strong> {{ agent.difficulty }}</li>
      </ul>
      <p class="hint">Astuce : ajoutez plus tard capacités, conseils, etc. (toujours en local)</p>
    </div>
  </div>
</template>

<style scoped>
.overlay {
  position: fixed;
  inset: 0; 
  background: rgba(0,0,0,.4);
  display: grid; 
  place-items: center;
}
.panel {
  width: min(560px, 92vw); 
  background: #fff; 
  border-radius: 12px; 
  padding: 16px;
}
.panel-header { 
  display: flex; 
  align-items: center; 
  justify-content: space-between; }
.close {
  border: none; 
  background: transparent; 
  font-size: 22px; 
  cursor: pointer;
}
.info { 
  list-style: none; 
  padding: 0; 
  margin: 8px 0 0;
  color : black }
.info li { 
  margin: 6px 0; 
}
.hint { 
  color: #666; 
  font-size: 14px; 
  margin-top: 12px; 
}
.nom-agent{
  color : black
}
</style>
