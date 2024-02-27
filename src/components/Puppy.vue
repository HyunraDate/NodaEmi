<script>
export default {
    props:['going']
    //第二种写法：props: {going: string} 
    //对于以对象形式声明中的每个属性，key 是 prop 的名称，而值则是该 prop 预期类型的构造函数。
    //比如，如果要求一个 prop 的值是 number 类型，则可使用 Number 构造函数作为其声明的值。
}
</script>

<template>
    <div class="going river">
        <h2>{{ going }}</h2>
        <button @click="$emit('enlarge-text')">Rhein</button> <!--子组件可以通过调用内置的 $emit 方法，通过传入事件名称来抛出一个事件
        因为有了 @enlarge-text="postFontSize += 0.1" 的监听，父组件会接收这一事件，从而更新 postFontSize 的值。-->
    </div>
</template>