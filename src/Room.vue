<template>
  <div>
    <img :src="oneRoom.image" class ="room-img">
    <h4>{{oneRoom.title}}</h4>
    <a>{{oneRoom.content}}</a>
  </div>
</template>

<script>
export default {
  props : {
    oneRoom : Object
  }
}

</script>

<style>

</style>