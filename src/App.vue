<template>

  <!-- 메뉴 -->
  <div class="menu">
        <a v-for="a in 메뉴들" :key="a">{{ a }}</a>
    </div>

  <Discount/>

  <!-- 모달창 -->
  <Modal/>


  <!-- 로고 및 내용 -->
  <img alt="Vue logo" src="./assets/logo.png">
  <div v-for="(원룸, i) in 원룸들" :key="i">
    <img :src="원룸.image" class="room-img">
    <h4 @click="모달창열렸니 = true; 누른거 = i">{{ 원룸.title }}</h4>
    <p>{{ 원룸.price }}원</p>
  </div>
</template>

<script>

import data from './oneroom';
import Discount from './components/Discount';
import Modal from './components/Modal';

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
