<template>
  <div class="black-bg" v-if="checkModal">
    <div class="white-bg">
        <img :src="oneRooms[roomNum].image" class="room-img">
        <h4>{{oneRooms[roomNum].title}} </h4>
        <p>{{oneRooms[roomNum].content}} </p>
        <input v-model.number="month">
        <p>{{oneRooms[roomNum].price * month}} 원</p>
        <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>
  
<script>
  export default {
      name : 'Modal',
      data(){
        return {
          month : 1
        }
      },
      watch : {
        month(a){
          if (isNaN(a)){
            alert("숫자만 ㅇㅇ");
            this.month = 1;
          }
        }
      },
        beforeUpdate(){
          if (this.month == 2){
            alert('22222');
            this.month = 3;
          }
      }
      ,
      props : {
        oneRooms : Array,
        roomNum : Number,
        checkModal : Boolean
      }
  }
</script>

<style>

</style>