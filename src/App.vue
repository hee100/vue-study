<template>
  <Discount v-if="showDiscount == true" />

  <transition name="fade">
    <Modal @closeModal="checkModal = false" :oneRooms="oneRooms" :roomNum="roomNum" :checkModal="checkModal"/>
  </transition>
  
  <div class="menu"> 
    <a v-for="menu in menus" :key="menu"> {{menu}}</a>
  </div>

  원룸샵
  <p>
     <button @click="priceSort">가격순 정렬</button>
  </p>
  <p>
     <button @click="priceSortR">가격 역순 정렬</button>
  </p>
  <p>
     <button @click="hangulSort">가나다 정렬</button>
  </p>


  <!-- <Room :oneRooms="oneRooms" :checkModal="checkModal"/> -->
  <Room @openModal="checkModal = true; roomNum = $event" :oneRoom="oneRooms[i]"
   v-for="(oneRoom, i) in oneRooms" :key="i"/>


  <!-- <div v-for="(oneroom, i) in oneRooms" :key=i>
    <img :src="oneRooms[i].image" class ="room-img">
    <h4 @click="checkModal = true; roomNum = i">{{oneRooms[i].title}}</h4>
    <a>{{oneRooms[i].content}}</a>
  </div> -->

</template>

<script>
import JSdatas from './assets/oneroom.js';
import discount from './discount.vue';
import room from './Room.vue';
import Modal from './Modal.vue'

export default {
  name: 'App',
  data(){
    return {
      showDiscount : true,
      menus : ['Home', 'Shop', 'About'],
      oneRooms : JSdatas,
      oneRoomsOrigin : [...JSdatas],
      checkModal : false,
      roomNum : undefined,
    }
  }, 
  methods: {
    priceSort() {
      this.oneRooms.sort(function(a,b){
          return a.price - b.price;
      })
    },
    priceSortR() {
      this.oneRooms.sort(function(a,b){
          return b.price - a.price;
      })
    },
    hangulSort() {
      this.oneRooms.title.sort();
    },
    rollBack(){
      this.oneRooms = [...this.oneRoomsOrigin];
    }
  },

  beforeUpdate(){
    if (this.month == 2){
      alert('2개월은 너무 적음.. 안팝니다')
    }
 },

  // mounted(){
  //   setTimeout(()=>{
  //     this.showDiscount = false;
  //   }, 1000);
  // },

  components: {
    Discount : discount,
    Room : room,
    Modal : Modal
  }
}
</script>

<style>
.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}

.fade-enter-from {
  transform: translateY(-1000px);
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: translateY(0px);
}


body {
  margin : 0
}
div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; padding: 20px;
}

.white-bg {
  width: 100%; background: white;
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
  color: #232628;
}

.menu {
  background: rgb(60, 211, 88);
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color : white;
  padding: 10px;
}

.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 0px;
}
</style> 
