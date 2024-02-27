<script>
import Content from "./components/Content.vue";
import { ref, reactive } from "vue";
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

  setup() {
    //组件被创建之前执行，不需要使用this, this不会指向实例 
    //set up里没有beforeCreate 和 created这两个钩子函数，因为可以替换掉了

    //here is msg 的逻辑代码
    console.log("setup"); 

    let msg = "Puppy♥"
    //因为是函数所以可以直接定义 const, 所以不用this了
    //But! Const不能改变，会报错滴！所以hier可以 let， 不报错但也不change，
    //But console.log work 说明数据不是响应式的. 不能及时反馈
    function changeMsg(){
      msg='be mine'
    }
    //if u want 响应式， use ref -> 去上面引入 import { Ref } from "vue"


    //不能向上面data那样直接调用，setup是局部作用域
    console.log(msg); //不是响应式
    //所以通过ref定义响应式变量

    // this is conter的逻辑代码
    const counter=ref(0) //ref()返回带有value属性的对象
    function changeCounter(){
      counter.value++
    }

    //通过reactive 定义引用类型的数据
    // this is obj的逻辑代码
    const obj=reactive ({ //hier传参
      name:"Emil",
      age:20,
      identity: {
        name: 'Patient'
      }
    })
    function changeObjName(){
      obj.name='Ada'
    }
    


    return {msg, changeMsg, counter, changeCounter, obj, changeObjName, ...obj }; //如果要使用要暴露出去
    //ps. 省略号here是扩展运算，...obj就是 name,age， 因为前面都有obj, 记得加空格

    return { msg, changeMsg }; //如果你要调用的话

  }
 }

</script>

<template>
<!--组件实例的所有property，无论如何定义，都可以在组件的模板中访问-->
   <div>
    <h2>{{ msg }}</h2>
    <button @click="changeMsg">change your mind</button>
    <h2>{{ counter }}</h2>
    <button @click="changeCounter">change counter</button>
    <h2>{{ obj }}</h2>
    <button @click="changeObjName">change your name</button>
    <h2>{{ obj.identity.name }}</h2>
    <Content :message="message"/> <!--这里是传参message : 是动态参数-->
    <button @click="message='call me'">Lose</button>
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
