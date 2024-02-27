<template>
    <!--私 树干组件-->
    <div>
        <!--组件是带有名称的可复用的实例，单独功能模块的封装-->
            <!--Content是父组件-->
            <!--Bye是子组件-->

            <!--父子组件的访问方式-->
            <!--父组件访问子组件： $refs-->
            <!--子组件访问父组件： $parent-->
            <!--子组件访问根组件： &root-->
        <p>---♥-----------------------------♥---</p>
        <h2>告别诗的组件</h2>
        <p>---♥-----------------------------♥---</p>
         <!--此处的template标签中的内容显示并且在dom中不存在template标签-->
        <h2>{{ name }}</h2>
        <button @click="msg='回电我'">message</button>
        <Bye></Bye>
        <button @click="sendme">send to form</button>

        <h2>{{ message }}</h2>
    </div>


</template>

<script>
import {inject} from 'vue'
import Bye from './Bye.vue'
export default {
    //props接受组件

    setup(){
        const name= inject ('name') //接受来自父组件send的name
        return{name}
    },

    //Data必须是一个函数，必须要返回一个对象
    //因为当Content为form的子组件时，form中用的Content是多个<Content></Content>都是独立的，
    //d.h.让每一个组件对象都返回一个新的对象，不会造成数据污染。
    data(){
        return{
            msg:"唔好再揾我"
        };
    },

    //moubted(){
    //    console.log(this.message);
    
    components:{
        Bye
    },
    methods:{
        //how to 自定义 (2 Steps)
        //1、在子组件中，通过$emit()来触发事件
        sendme:function(){
            //this.$emit('事件的名称','发送的时间参数')
            this.$emit('injectMsg', this.msg) //hier是自定义的事件名称

        }
    },
}

</script>
