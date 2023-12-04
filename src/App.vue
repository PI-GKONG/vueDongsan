<template>

  <transition name="fade">
    <Modal @closeModal = "state = false" :onerooms="onerooms" :state="state" :clickId="clickId" />
  </transition>

  <div class="menu">
  <a v-for="(a, i) in menus" :key='i'>{{ a }}</a>
  </div>

  <Discount />

  <button @click="priceSortDown()">가격 낮은 순 정렬</button>
  <button @click="priceSortUp()">가격 높은 순 정렬</button>
  <button @click="sortBack()">되돌리기</button>
  
  <Card @openModal = "state = true; clickId = $event" :oneroom="onerooms[i]" 
    v-for="(oneroom, i) in onerooms" :key="oneroom"
  />

</template>

<script>

  import data from './assets/oneroom.js'
  import Discount from './components/Discount.vue'
  import Modal from './components/Modal.vue'
  import Card from './components/Card.vue'

  export default {
    name: 'App',
    data() {
      return {
        oneroomsOrigin : data,
        onerooms : data,
        state : false,
        menus : ['Home', 'Products', 'About'],
        clickId : 0
      }
    },
    methods : {
      increase(i) {
        this.reportNum[i] += 1;
      },
      priceSortDown() {
        this.onerooms.sort(function(a, b) {
          return a.price - b.price
        }) 
      },
      sortBack() {
        this.onerooms = this.oneroomsOrigin;
        hjps.s;glll
        }
    },
    components: {
      Discount : Discount,
      Modal : Modal,
      Card : Card,
    }
  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.start {
  opacity: 0;
  transition: all 0.5s;
}

.stop {
  opacity: 1;
}

.fade-enter-from {
  transform: translateY(-1000px);
  opacity: 0;
}

.fade-enter-active {
  transition: all 0.5s;
}

.fade-enter-to {
  transform: translateY(0px);
  opacity: 1;
}

.fade-leave-from {
  transform: translateY(0px);
  opacity: 1;
}

.fade-leave-active {
  transition: all 0.5s;
}

.fade-leave-to {
  transform: translateY(-1000px);
  opacity: 0;
}

.discount {
  background-color: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}

.black-bg {
  width: 100%;
  height: 100%;
  background-color: rgba(0,0,0,0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background-color: white;
  border-radius: 8px;
  padding: 20px;;
}

.menu {
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}


</style>
