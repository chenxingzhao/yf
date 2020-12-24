<template>
  <div>
    <p>男士：￥{{source.manPrice}} <button @click="jian('man')">-</button>{{num.man}}<button @click="add('man')">+</button></p>
    <p>女士：￥{{source.womanPrice}} <button @click="jian('woman')">-</button>{{num.woman}}<button @click="add('woman')">+</button></p>
    <p>儿童：￥{{source.childPrice}} <button @click="jian('child')">-</button>{{num.child}}<button @click="add('child')">+</button></p>
  </div>
</template>

<script>
  export default {
    name: "SourceCom",
    props:{
      source:{},
      num:{}
    },
    methods:{
      jian(value){
        this.$emit('jians',value)
      },
      add(value){
        this.$emit('adds',value)
      }
    }
  }
</script>

<style scoped>

</style>