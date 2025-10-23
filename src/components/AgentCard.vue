<script setup>
const props = defineProps({
  name: { type: String, required: true },
  role: { type: String, required: true },
  difficulty: { type: String, required: true },
  image: { type: String, required: true } 
})
const emit = defineEmits(['select'])

function onClick() {
  emit('select')
}
</script>

<template>
  <button class="card" @click="onClick">
    <img :src="image" :alt="`Image de ${name}`" class="agent-image" />
    <div class="div">
      <h3 class="title">{{ name }}</h3>
      <span class="role">{{ role }}</span>
    </div>
    <p class="difficulty" :class="{ hard: difficulty === 'Difficile', easy: difficulty === 'Facile' }">
      Difficulté : {{ difficulty }}
    </p>
  </button>
</template>

<style scoped>
.card {
  text-align: left;
  width: 100%;
  border: 1px solid #eee;
  border-radius: 10px;
  padding: 14px;
  cursor: pointer;
  background: #fff;
}
.card:hover { 
  border: 5px solid #FF4656;
}
.div {
  display: flex; 
  align-items: center; 
  justify-content: space-between;
}
.title { margin: 0; 
  font-size: 18px; 
}
.role {
  font-size: 12px; 
  padding: 4px 8px; 
  border: 1px solid #ddd; 
  border-radius: 999px;
}
.difficulty { margin: 8px 0 0; 
  font-size: 14px; 
}
.easy { 
  color: #2d8a5f; 
}
.hard { 
  color: #c04848; 
}
.agent-image{
  width: 100%;
}
</style>
