<script setup>
defineProps({
  title: {
    type: String,
    required: true,
  },
})
</script>

<template>
  <header class="header">
    <img src="../assets/images/header.jpg" class="header__image" alt="header du site avec comme titre Valorant Agents/Stats">
    <h1 class="header__title">{{ title }}</h1>
  </header>
</template>

<style scoped>
.header {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 12px;
  margin-bottom: 24px;
}

.header__image {
  width: 100%;
  max-width: 900px;
  border-radius: 12px;
  object-fit: cover;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}

.header__title {
  font-size: 2rem;
  font-weight: 700;
  color: #FF4656;
}
</style>
