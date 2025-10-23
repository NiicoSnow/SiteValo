<script setup>
const props = defineProps({
  agent: {
    type: Object,
    required: true
  }
})
const emit = defineEmits(['close'])
</script>

<template>
  <div class="overlay" @click.self="emit('close')">
    <div class="panel">
      <header class="panel-header">
        <img :src="agent.image" :alt="`Image de ${name}`" class="agent-image-panel" />
        <h2 class="nom-agent">{{ agent.name }}</h2>
        <button class="close" @click="emit('close')">×</button>
      </header>
      <ul class="info">
        <li><strong>Rôle :</strong> {{ agent.role }}</li>
        <li><strong>Difficulté :</strong> {{ agent.difficulty }}</li>
      </ul>
      <p class="info-desc">{{agent.text}}</p>
      <div v-if="agent.video" class="video-container">
        <iframe
          :src="agent.video"
          frameborder="0"
          allowfullscreen
          allow="autoplay; encrypted-media"
        ></iframe>
      </div>
    </div>
  </div>
</template>

<style scoped>
.video-container {
  position: relative;
  padding-bottom: 56.25%;
  height: 0;
  overflow: hidden;
  border-radius: 1rem;
  margin: 1rem 0;
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.4);
}
.video-container iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
strong{
  font-weight: 700;
}
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
  justify-content: space-between; 
}
.close {
  border: none; 
  background: transparent; 
  font-size: 22px; 
  cursor: pointer;
  align-self: baseline;
}
.info { 
  list-style: none; 
  padding: 0; 
  margin: 8px 0 0;
  color : black }
.info li { 
  margin: 6px 0; 
}
.info-desc { 
  color: black; 
  font-size: 14px; 
  margin-top: 12px; 
}
.nom-agent{
  color : black;
  font-size: 32px;
}
.agent-image-panel{
  width: 25%;
}
</style>
