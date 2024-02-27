<template>
    <!--私 树枝组件-->
    <div>
        <!-- ByeBye // dont want it-->
        <h2>{{ callme }}</h2>
        <h2>{{ kato }}</h2>
        </div>
</template>

<script>
export default {
    //props:['callme','kato'] hier ist 字符串数组， 多种类型就数组。
    pros:{ //对象用的最多
        //1、类型的限制
        //message: String //maomao绿色的
        //2、除了类型限制，还可以设置默认值
        message:{ 
            type: String,
            default:"Saturday",
            required:true //required是布尔boolan值，这里是一定给我传 （必传值）
        }
    }
}
</script>