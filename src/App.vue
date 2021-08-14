<template>

<!-- 메뉴 -->
<div class="menu">
      <a v-for="a in 메뉴들" :key="a">{{ a }}</a>
  </div>

<!-- 할인 -->
<Discount :할인율="할인율" />

<button @click="priceSort">가격순정렬</button>
<button @click="sortBack">되돌리기</button>


<!-- 모달창 -->
<transition name="fade">
  <Modal @closeModal="모달창열렸니=false" :원룸들="원룸들" :누른거="누른거" v-if="모달창열렸니" />
</transition>

<!-- 로고 및 내용 -->
<Card @openModal="모달창열렸니=true; 누른거=$event" :원룸="원룸" v-for="원룸 in 원룸들" :key="원룸" />

</template>

<script>

import data from './oneroom';
import Discount from './components/Discount';
import Modal from './components/Modal';
import Card from './components/Card';

export default {
  name: 'App',
  data() {
    return {
      할인율: 30,
      원룸들오리지널: [...data],
      누른거 : 0,
      원룸들: data,
      모달창열렸니: false,
      신고수 : [0, 0, 0],
      메뉴들: ['Home', 'Shop', 'About'],
      products: ['역삼동원룸', '천호동원룸', '마포구원룸'],
    }
  },
  methods: {
    priceSort() {
      this.원룸들.sort(function(a, b){
        return -(a.price-b.price);
      });
    },
    sortBack() {
      this.원룸들 = [...this.원룸들오리지널];
    },
  },
  mounted() {
    setInterval(() => {
      this.할인율--;
    }, 1000)
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

.fade-enter-from {
  transform: translateY(-1000px);
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  transform: translateY(0);
}

.fade-leave-from {
  transform: translateY(0);
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  transform: translateY(-1000px);
}

</style>
