<template>
  <div class="discount">
    <h4>결제시 {{amount}}% 할인</h4>
  </div>
</template>

<script>
export default {
    name: 'discount',
    data(){
      return {
        amount : 30,
      }
    }
}
</script>

<style>

</style>