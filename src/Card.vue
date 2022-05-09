<template>
  <div>
    <img :src="원룸들.image" class="roomimg" />
    <h4 @click="$emit('openModal', 원룸들.id)">{{ 원룸들.title }}</h4>
    <p>{{ 원룸들.price }}원</p>
  </div>
</template>

<script>
export default {
  name: "t_Card",
  props: {
    원룸들: Object,
  },
};
</script>

<style>
</style>