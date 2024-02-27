<script setup>
//定义响应式变量，还需要从vue中引入
import { provide, ref } from 'vue';
//用setup语法糖引入就不需要再注册啦~
import Content_provide from './components/Content_provide.vue';
//定义变量，在模板中使用不需要暴露啦，可直接使用
//私 根组件(root) （所以内容都是通过form.vue展示在页面上）

const name=ref('Cookie can') //if you want 响应式要这里ref定义，因为inject不是响应式的
    provide('name', name) //传去子组件
    function changeName(){
      name.value='ice cream ♡'
    }
    // return {changeName}; 语法糖也不需要返回函数啦，return也不被需要了

/* 注册和data 已经不被需要了
export default {
  data(){
    return{
      message:"回电我",

    };
  },
  
  //为了增加provide值和inject值之间的响应式，可在provide值时使用ref和reactive
  setup(){
    const name=ref('Cookie can') //if you want 响应式要这里ref定义，因为inject不是响应式的
    provide('name', name) //传去子组件
    function changeName(){
      name.value='My man'
    }
    return {changeName};
  },
  components:{
    Content_provide
  },

};
*/

</script>

<template>
<!--组件实例的所有property，无论如何定义，都可以在组件的模板中访问-->
  <!--form是父组件-->
  <!--Content是子组件-->
  <div>
    <!--虽然都系同一个content，但系只会改变你click嘅葛个，因为每次Content返回数据的对象都是新的对象-->
    <!--就是上面点改变，下面都系互不干扰的，唔会变-->
    <!--This is 数据储存-->
    
    <!--wanna get 子组件Content的数据，通过自定义事件-->
    <!--how to 自定义-->
    <!--2、在父组件在，通过v-on监听子组件中自定义事件，in methods-->
    <!--<Content @injectMsg="getChildMsg"></Content>-->
    <p>♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥</p>
    <Content_provide/>
    <button @click="changeName">change your mind</button>
    <h2>{{ message }}</h2>
    
    
    <!--<Content></Content>-->
    <!--<Content></Content>-->


  </div>
</template>

<style>

</style>
