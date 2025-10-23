<script setup>
defineProps({
  footer__title: {
    type: String,
    required: true,
  },
})
</script>

<template>
  <footer class="footer">
    <h2 class="footer__title">{{ footer__title }}</h2>
  </footer>
</template>

<style scoped>
.footer{
    width: 100%;
    height: 200px;
    background-color:#FF4656;
    border-radius: 12px;
}
.footer__title{
    color : #0F1923;
    margin : 24px
}
</style>
