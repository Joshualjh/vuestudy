<template>
  <div v-if="modal_status == true" class="black-bg">
    <div class="white-bg">
      <h3>{{ 원룸들[k].title }}</h3>
      <img :src="원룸들[k].image" class="madal_room" />
      <p>{{ 원룸들[k].content }}</p>
      <input v-model="month" />
      <p>{{ month }}개월 선택함 : {{ 원룸들[k].price * month }}원</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "_Modal",
  data() {
    return {
      month: 3,
    };
  },
  watch: {
    month(a) {
      if (isNaN(a) == true) {
        alert("문자입력하지마세요");
        this.month = 1;
      }
    },
  },
  props: {
    원룸들: Array,
    modal_status: Boolean,
    k: Number,
  },
  beforeUpdate() {
    if (this.month < 3) {
      alert("3개월 부터 가능합니다.");
      this.month = 3;
    }
  },
};
</script>

<style>
</style>