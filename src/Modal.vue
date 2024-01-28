<template>
  <div class="black-bg" v-if="checkModal">
    <div class="white-bg">
        <img :src="oneRooms[roomNum].image" class="room-img">
        <h4>{{oneRooms[roomNum].title}} </h4>
        <p>{{oneRooms[roomNum].content}} </p>
        <p>{{oneRooms[roomNum].price}} 원</p>
    </div>
  </div>
</template>
 
<script>
export default {
    name : 'Modal',
    props : {
      oneRooms : Array,
      roomNum : Number,
      checkModal : Boolean
    }
}
</script>

<style>

</style>