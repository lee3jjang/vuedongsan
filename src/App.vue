<template>

  <!-- 메뉴 -->
  <div class="menu">
        <a v-for="a in 메뉴들" :key="a">{{ a }}</a>
    </div>

  <Discount />

  <!-- 모달창 -->
  <Modal @closeModal="모달창열렸니=false" :원룸들="원룸들" :누른거="누른거" v-if="모달창열렸니" />

  <!-- 로고 및 내용 -->
  <Card @openModal="모달창열렸니=true; 누른거=i" :원룸="원룸" v-for="(원룸, i) in 원룸들" :key="i" />
</template>

<script>

import data from './oneroom';
import Discount from './components/Discount';
import Modal from './components/Modal';
import Card from './components/Card';

export default {
  name: 'App',
  data(){
    return {
      누른거 : 0,
      원룸들: data,
      모달창열렸니: false,
      신고수 : [0, 0, 0],
      메뉴들: ['Home', 'Shop', 'About'],
      products: ['역삼동원룸', '천호동원룸', '마포구원룸'],
    }
  },
  methods: {
  },
  components: {
    Discount,
    Modal,
    Card,
  }
}
</script>

<style>
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
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
</style>
