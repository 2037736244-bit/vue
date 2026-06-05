<template>
    <TagInput/>
</template>

<script lang = "ts">
    import Calculator from './components/Calculator.vue'
    import TagInput from './components/TagInput.vue'
    export default{
        name:'App',
        //组件注册
        components:{
            Calculator,
            TagInput
        }
    }
</script>
 
<style>

</style>