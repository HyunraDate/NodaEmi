<script>
import HelloWorld from './components/HelloWorld.vue'
//计算属性
export default {
  data(){
    return{
      message:"会いたいな しか出ない",
      age:0
    }
  },

  //this指当前组件，根组件

  computed:{ //计算属性 (有依赖值，只要依赖值不变就不会重新计算) hier是简写
    reverseMsg:function(){ //hier reverseMsg依赖下面的message
      return this.message.split('').reverse().join('')
    }
     
  },
  //每一个计算属性都有getter和setter
  //完整的写法：
  /*
  reverseMsg: {
    get: function(){
      return this.message.split("").reverse().join("");
    },
  }

  */

  methods: {
    reverseMessage:function(){
      return this.message.split('').reverse().join('')
    }

  },
};
</script>

<template>
<!--组件实例的所有property，无论如何定义，都可以在组件的模板中访问-->
  <div>
    <p>{{ message}}</p>
    <!--Way1, JS 表达式，共计算三次-->
    <p>{{ message.split('').reverse().join('')}}</p>
    <p>{{ message.split('').reverse().join('')}}</p>
    <p>{{ message.split('').reverse().join('')}}</p>
    <!--Way2, 计算属性, 不会从新计算，所以只有一次，hier just 结果缓存-->
    <p>{{ reverseMsg }}</p>
    <p>{{ reverseMsg }}</p>
    <p>{{ reverseMsg }}</p>
    <!--Way3, 使用method中的方法--> 
    <p>{{ reverseMessage() }}</p>
    <p>{{ reverseMessage()}}</p>
    <p>{{ reverseMessage() }}</p>
    <button @click="message='君よりもっと 素敵なひとも'">change your message</button>
  </div>
</template>

<style>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
