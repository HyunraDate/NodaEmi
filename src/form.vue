<script>
import Content from './components/Content.vue'
//私 根组件(root) （所以内容都是通过form.vue展示在页面上）
export default {
  data(){
    return{
      message:"lose",

    }
  },
  components:{
    Content
  },

  /*methods: {
    //给vue定义方法 
    getChildMsg:function(value){ //hier value是默认值
      console.log(value);
      this.message=value

    }*/
};
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
    <Content @injectMsg="getChildMsg"></Content>
    <p>♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥</p>
    <h2>{{ message }}</h2>
    
    
    <!--<Content></Content>-->
    <!--<Content></Content>-->


  </div>
</template>

<style>

</style>
