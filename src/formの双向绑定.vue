<script>
import HelloWorld from './components/HelloWorld.vue'
//声明式渲染 提高开发效率 formの双向绑定
export default {
  data(){
    return{
      counter:11.12,
      msg:"hey! 我们来的时候好像是一起来的欸?"
    }
  },
  methods: {
    //给vue定义方法
    changeValue(){
      console.log(是啊);
    },

  },
};
</script>

<template>
<!--组件实例的所有property，无论如何定义，都可以在组件的模板中访问-->
  <div>
    <input type="text" v-model="msg">
    <h2>{{ msg }}</h2> 
    <!--here就是双向绑定，text都可以改变上面data的msg
    v-model本质上是语法糖，负责监听用户的输入事件来更新数据-->
    <!--v-model原理-->
    <!--本质是两个操作
      1。v-bind绑定一个value属性
      2.v-on给当前元素添加一个input事件
      -->
      <!-- <input type="text" :value="msg"> 这里就绑定了value和msg啦，不绑定就要msg再打一次啦，but不是双向哦-->
      <!--Way2-->
      <input type="text" :value="msg" @input="changeValue">


  </div>
</template>

<style scoped>

</style>
