<template>
  <div
    v-if="modal_status == true"
    class="black-bg"
    @click="$emit('closeModal')"
  >
    <div class="white-bg">
      <h3>{{ 원룸들[k].title }}</h3>
      <img :src="원룸들[k].image" class="madal_room" />
      <p>{{ 원룸들[k].content }}</p>
      <p>{{ 원룸들[k].price }}원</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "_Modal",
  props: {
    원룸들: Array,
    modal_status: Boolean,
    k: Number,
  },
};
</script>

<style>
</style>