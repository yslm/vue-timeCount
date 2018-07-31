<template>
  <div class="test">
    <countEl :endTime="endTime" :callback="callback1"></countEl>
    <p>sssssssssssssssssssssssss</p>
    <countEl :endTime="endTime2" :callback="callback1"></countEl>
  </div>
</template>
<script>
    import countEl from './CountDown.vue'
  export default {
    data(){
      return {
        endTime:'7/31/2018 14:33:00',
        endTime2:'7/31/2018 14:38:00',
      }
    },
    methods:{
      callback1(){
        console.log('执行回调');
      }
    },

    components:{
      countEl
    }
  }
</script>
<style></style>
