<template>
  <div class="black-bg" v-if="checkModal">
    <div class="white-bg">
        <img :src="oneRooms[roomNum].image" class="room-img">
        <h4>{{oneRooms[roomNum].title}} </h4>
        <p>{{oneRooms[roomNum].content}} </p>
        <p>{{oneRooms[roomNum].price}}원</p>
        <p>
            <button @click="checkModal = false">닫기</button>
        </p>
    </div>
  </div>
</template>

<script>
export default {
    name : 'Modal'
}
</script>

<style>

</style>