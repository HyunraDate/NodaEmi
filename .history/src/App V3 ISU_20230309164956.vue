<script>
import { ref, reactive, watch, watchEffect } from "vue";
export default {
  data(){
    return{
      massage:"hey you!"
    }
  },
  /* This is V2 旧写法
    methods: {
    //给vue定义方法
    changeUname:function(){
      //this 指向vue实例
      this.uname='Takase Toya'
    },
    changeColor:function(){
      this.id='Tonight2'
    } */
   
  //组合式API，将同一个逻辑关注点相关代码收集在一起
  //msg是逻辑代码
  //操作msg

  setup(){
    const counter=ref(0)
    function changeCounter(){
      counter.value++
    }
    const user=reactive({
      name:"高析羽",
      age:20
    })
    function changeUserName(){
      user.name="毛欣宇"
    }
    //watch（监听的响应式应用，回调函数）
    watch(counter,(newVal,oldVal)=>{
      console.log("newVal-----",newVal);
      console.log("oldVal-----",oldVal);
    });
    //watchEffect（回调函数）注意不需要指定监听的属性，自动收集依赖
    watchEffect(()=>{
      console.log(user.name);
    })
    return{counter,user,changeCounter,changeUserName};
  },

  //选项式API
  watch:{
    message:function(newVal,oldVal){
    }
  }
}
</script>

<template>
   <div>
    <h2>{{ counter }}</h2>
    <button @click="changeCounter">change your counter</button>
    <h2>{{ user.name }}</h2>
    <button @click="changeUserName">change user name </button>
   </div>

</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
#Tonight{
  color:rgb(95, 116, 126);
}
#Tonight2{
  color:rgb(160, 43, 68);
}
.Tonight{
  font-size:50px;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
