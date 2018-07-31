<template>
  <!--倒计时组件
  逻辑是设置好一个截止时间，然后每次进去都开始进行倒计时计算，这个反应比较快，比较了另外一个定时器的实现，这个比较快速
  -->
  <div class="count-down">
    <p>距离结束还有多长时间</p>
    <p class="mytime" v-if="content">{{content}}</p>
  </div>
</template>
<script>
  export default {

//    props:['endTime','callback'],
    props:{
      endTime:{
        type: String,
        default :'',
        require:true
      },
      callback : {
        type : Function
      }
    },
    data(){
      return{
        count:0,  //这个就是用于倒计时 减去的数，因为count每一秒都会加1就相当于时间自动走了1秒，这样就不用每次都去获取当前时间，不过这个时间不会特别精确
        orderTime:null, //这个参数是定义定时器的时间
        content:''//这个用于显示倒计时的时间以及结束后的文案
      }
    },
    methods:{
      /*获取服务器的当前时间*/
      getUTC(){
        return +new Date();
      },
      /*这里使用了两种，一种是setinterval，一种是timeout，现在使用的是settimeout*/
      countDown(){
        var d=0,h=0,m=0,s=0,
          deadline=+new Date(this.endTime),
          now=this.getUTC(),
          diff=(deadline-now)/1000;
        console.log(deadline,'截止时间，就是个时间戳，并且需要的就是时间戳');
        console.log(now,'now');
        var self=this;
        if(diff<=0){
          self.content='时间已过'
          clearTimeout(self.orderTime);
          self._callback();
        }
        function showTime() {
          self.count++;
          var ts=diff-self.count;
          console.log(self.count,ts);
          if(diff<=0)return;//如果外面已经判断过diff小于0了，
          if(ts<0){
            self.content='时间已过'
            clearTimeout(self.orderTime);
            self._callback();
            return
          }

          var d=parseInt(ts/86400,10);//天
          var h=parseInt(ts / 60 / 60 % 24,10)   //时
          var m=parseInt(ts/60%60,10);//分钟
          var s=parseInt(ts%60,10)  //秒
          self.content=`${d}天${h}时${m}分${s}秒`
          self.orderTime=setTimeout(showTime,1000)
        }
        showTime();

      },
      _callback(){
        if(this.callback && this.callback instanceof Function){
          this.callback(...this);
        }
      }
    },
    mounted(){
       this.countDown();
    },
    beforeDestroy(){
      this.count=0;
//    clearInterval(this.orderTime);
      clearTimeout(this.orderTime);
      console.log('停止定时器',this.orderTime);
      /*停止定时器*/
    }
  }


</script>
<style>
  .mytime{
    /*color: #fff!important;*/
    color: #000;
  }

</style>
