<template>
  <div class="hello">
    <h2>Essential Links</h2>
    <!--<countEl :endTime="endTime"></countEl>-->

    <countEl :endTime="1533010440+''" :callback="callback" ></countEl>
    <countEl :endTime="1633037800+''" :callback="callback" ></countEl>
    <!--<count-down endTime="1490761620" :callback="callback" endText="已经结束了"></count-down>-->


    <router-link to="test">跳转</router-link>
  </div>
</template>

<script>


//  import countEl from './CountDown.vue'
  import countEl from './testcount.vue'
export default {
  name: 'HelloWorld',
  data () {
    return {
      endTime:'7/31/2018 16:50:00',
      endTime2:'7/31/2018 19:50:00',

    }
  },
  methods:{
    callback(){
      console.log(55555);
    }
  },
  components:{
    countEl
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
