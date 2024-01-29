<template>
  <Discount/>
  <Modal @closeModal="checkModal = false" :oneRooms="oneRooms" :roomNum="roomNum" :checkModal="checkModal"/>
  
  <div class="menu"> 
    <a v-for="menu in menus" :key="menu"> {{menu}}</a>
  </div>

  원룸샵

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
      menus : ['Home', 'Shop', 'About'],
      oneRooms : JSdatas,
      checkModal : false,
      roomNum : undefined
    }
  }, 
  methods: {
  },
  components: {
    Discount : discount,
    Room : room,
    Modal : Modal
  }
}
</script>

<style>

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
