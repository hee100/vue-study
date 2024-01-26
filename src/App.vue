<template>
  <div class="menu">
    <a v-for="a in menus" :key="a"> {{a}}</a>
  </div>
    원룸샵 

  <div v-for="(product, i) in products" :key="i">
    <h4> {{products[i]}} </h4>
    <p> {{prices[i]}}만원</p>
    <button @click="increase(i)">허위매물신고</button> <span>신고수 : {{count[i]}}</span>
  </div>  
  <!-- <div>
    <h4> {{products[1]}}</h4>
    <p> 70 만원</p>
  </div>
  <div>
    <h4> {{products[2]}}</h4>
    <p> 90 만원</p>
  </div> -->
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      count : [0,0,0],
      prices : [50,80,90],
      menus : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸']
    }
  }, 
  methods: {
    increase(i){
      this.count[i]++;
    }
  },
  components: {
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

.menu {
  background: darkgoldenrod;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color : white;
  padding: 10px;
}
</style> 
