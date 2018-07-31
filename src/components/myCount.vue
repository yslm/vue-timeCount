<template>
  <div class="my-count">

    <p>距离结束还有多久</p>
    <p>{{content}}</p>

  </div>

</template>
<script>
  //整个逻辑就是通过定时器不断获取当前时间，然后取得时间差
  export default {
    props:['endTime'],
    data(){
      return{
        orderTime:null,//指定定时器的初始值
      }
    },
    methods:{

    },
    mounted(){

    },
    beforeDestroy(){


    }
  }

</script>
<style></style>
