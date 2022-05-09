<template>
  <!-- 모달창 -->
  <Modal
    @closeModal="modal_status = false"
    :원룸들="원룸들"
    :modal_status="modal_status"
    :k="k"
  />

  <!-- 메뉴 -->
  <div class="menu">
    <a v-for="작명 in menus" :key="작명">{{ 작명 }}</a>
  </div>

  <Discount />

  <!-- 본문 -->
  <Card
    @openModal="
      modal_status = true;
      k = $event;
    "
    :원룸들="원룸들[n]"
    v-for="(i, n) in 원룸들"
    :key="i"
  />

  <!-- <div v-for="(a, i) in 원룸들" :key="i">
    <img :src="원룸들[i].image" class="roomimg" />
    <h4 @click="(modal_status = true), (k = i)">{{ 원룸들[i].title }}</h4>
    <p>{{ 원룸들[i].price }}원</p>
  </div> -->
</template>

<script>
import data from "./assets/data";
import Card from "./Card.vue";
import Discount from "./discount1.vue";
import Modal from "./modal.vue";

export default {
  name: "App",
  data() {
    return {
      원룸들: data,
      price: [60, 70, 80],
      products: ["천호동원룸", "무실동원룸", "강남역원룸"],
      menus: ["Home", "Products", "About"],
      신고수: [0, 0, 0],
      modal_status: false,
      k: 0,
    };
  },
  methods: {
    increase() {
      this.신고수 += 1;
    },

    modal_move() {
      this.modal = true;
    },
  },

  components: {
    Discount,
    Modal,
    Card,
  },
};
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.Discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
.madal_room {
  width: 100%;
  margin-top: 20px;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
.roomimg {
  width: 100%;
  margin-top: 40px;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
