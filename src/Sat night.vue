<script>
//土曜の夜
import Puppy from './components/Puppy.vue';

export default {
    componts: {
        Puppy
    },
    data() {
        return {
            posts: [
                { id: 1, going: "Have a drink" },
                { id: 2, going: "Tonkatsu" },
                { id: 3, going: "Stay" }
            ],
            postFontSize:1
        };
    },
    components: { Puppy }
}
</script>

<template>
    <div :style="{ fontSize: postFontSize + 'em'}"> 
    <!--组件实例提供了一个自定义事件系统。父组件可以通过 v-on 或 @ 来选择性地监听子组件上抛的事件，
        就像监听原生 DOM 事件那样：-->
    <Puppy
    v-for="post in posts"
    :key="post.id"
    :going="post.going"
    @enlarge-text="postFontSize += 0.1"
    ></Puppy> <!--子组件可以通过调用内置的 $emit 方法，通过传入事件名称来抛出一个事件：-->
    </div>
</template>