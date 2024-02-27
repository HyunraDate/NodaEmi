<script>
import HelloWorld from './components/HelloWorld.vue'
//声明式渲染 提高开发效率
export default {
  data(){
    return{
      num:11.12,
      uname: "Emi Noda",
      id:"Tonight",
      url:'https://is3-ssl.mzstatic.com/image/thumb/Music116/v4/f2/c1/39/f2c139e1-bee3-ee5e-e39c-e7d4070c190d/859757815340_cover.jpg/600x600bf-60.jpg',
      attributeName:'id',
      mouseEvent:"click"
    }
  },
  methods: {
    //给vue定义方法
    changeUname:function(){
      //this 指向vue实例
      this.uname='Takase Toya'
    },
    changeColor:function(){
      this.id='Tonight2'
    }
  },
};
</script>

<template>
<!--组件实例的所有property，无论如何定义，都可以在组件的模板中访问-->
  <div>
     <!--{{ }} 双大括号是 Mustache语法哦~-->
    <p>{{num}}</p>
    <p>{{uname}}</p>
  </div>
  <!--v-onve: 当数据海边是，插值处的内容不会更新-->
  <p v-once>{{ uname }}</p>
  <button @click="changeUname">change your name</button>

  <!--v-bind：动态绑定属性内容-->
  <p v-bind:id="id">v-bind绑定</p>
  <img v-bind:src="url">
  <button @click="changeColor">change your color</button>
  <button @click="id='Tonight2'">change your color</button>

  <!--使用javascript表达式-->
  <p>{{ num+1}}</p>
  <p>{{uname.split('').reverse().join('') }}</p>
  <!--v-bind 语法糖：冒号啦-->
  <!--v-on：监听DOM事件-->
  <button v-on:click='changeColor'>change your name</button> <!--hier v-on：就是上面@的语法糖-->

  <!--动态参数-->
  <!--动态属性-->
  <p v-bind:[attributeName]="id">v-bind绑定</p>
  <button @click="attributeName='class'">change your attribute </button>

  <!--动态事件--> 
  <button @[mouseEvent]="attributeName='class'">change your attribute </button>
  <button @click="mouseEvent='mouseover'">change your event</button>
  

  <HelloWorld msg="Vite + Vue" />
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
