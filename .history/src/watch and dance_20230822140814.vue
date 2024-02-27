<script>
import HelloWorld from './components/HelloWorld.vue'
//声明式渲染 提高开发效率
export default {
  data(){
    return{
      message: "ほろよい",
      user:{
        name:"高析羽"
      },
      activeColor: '#89CFF0',
      fontSize: '20px',
      bgcColor: '#febdf8',
      styleObj: {
        color: '#88CB9D',// 423 //'#89CFF0',
        fontSize:'20px',
        "background-color": '#FCDFF3'//'#FCD3D1' //'#FE929F'Millennial Pink //'#febdf8'
      },  //if 前缀太多styleObj放里度， 后面直接用styleObj就得啦
      Dating:{date:"12.11.2022", plate:"Düsseldorf", word:"Sober"},
      now:"Tonight",

      num:1,
    };
  },
 
  methods: {
    feeling:function(){
      this.Dating.unshift('天亮之前一直和我跳舞吧！')
    },
    //因为unshift只能改变数组，Dating唔系数组！所以Error,所以直接 <li v-for="(i, index1) in num" :key='index1'>天亮之前一直和我跳舞吧！</li>
    
    /*feeling(){
      this.num++
    }
    */
  },

  watch:{ //监听数据变化
    //每当message变化是就会调用这个函数
    message:function(newValue, oldValue){
      console.log(newValue);
      console.log(oldValue);
      //with that实行异步操作or复杂逻辑代码
    },

    /*user:function(newValue){
      console.log(newValue);
    }
    */

    //when we need 深度监听deep, deep is 布尔类型Boolean 表示是否需要深度监听
    user:{
      handler:function(newValue){
        console.log(newValue);
      },
      deep: true, //i wanna deep watch,监听器会一层层向下监听，给对象每个属性都加上监听器
    }

  }
};
</script>

<template>
<!--组件实例的所有property，无论如何定义，都可以在组件的模板中访问-->
  <div>
    <p>{{ message }}</p>
    <button @click="message='hey yeah!'">change your message</button>
    <!--v-model数据的双向绑定-->
    <!--d.h 我在v-model的输入框改变message的话，上面data的message也会改变-->
    <input type="text" v-model="message"> 
    <p>{{ user.name }}</p>
    <button @click="user.name='Puppy'">change your name</button>
    <!--but监听不到对象属性的变化，so we need深度监听-->

    <!--Style样式的多种操作Ways-->
    <p :style="styleObj">楽しいまで 思えるには まだ酔いが足りないよ</p> 
    <!--This is 驼峰语法
    :style 支持绑定 JavaScript 对象值，对应的是 HTML 元素的 style 属性：
    CSS property 名可以驼峰式（camelCase）或者短横线分隔（kebab-case），记得用引号括起来命名；
    <p :style="{key(css属性名):value(属性值，来着Data中的属性)}"></p>-->
    <!--ps点解background-color要''，因为有-连词符号，用'background-color'as a string-->
    <!--if前缀太多，将Style的元素放在上面Data度-->

    <!--v-for 使用对象, item表示键值，key表示键名
    你也可以使用 v-for 来遍历一个对象的所有属性。遍历的顺序会基于对该对象调用 Object.keys() 的返回值来决定。-->
    <ul style="list-style-type: none">
      <li v-for="item in Dating" :key="item">{{ item }}</li>
      <!--<li v-for="(item,key) in Dating" :key="key">{{ item }}->{{ key }}</li>-->
      
      <!--换一种方法，因为不想先把话说出来
        <li v-for="(i, index1) in num" :key='index1'>天亮之前一直和我跳舞吧！</li>
        -->
    </ul>

    <p>{{ now }}</p>
    <button @click="now='天亮之前一直和我跳舞吧！'">tell me</button>
    
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
  filter: drop-shadow(0 0 2em fuchsia);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #89CFF0);
}

</style>
