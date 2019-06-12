<template>
<div class="inputWrapper">
  <input type="text" v-model="text">
  <button @click="addTodo">添加</button>
</div>
</template>
<script lang="ts">
import { Component, Vue, Mixins } from 'vue-property-decorator';
@Component
export default class NewTodo extends Vue {
  text:string = ''
  addTodo(){
    if(this.text===''){
        alert('输入不能为空')
        return;
    }
    this.$emit('addTodo', this.text)
    this.text = ''
  }
}
</script>

<style scoped lang="scss">
.inputWrapper { 
    display: flex;
    justify-content: center;
    justify-items: center;
    input{
        line-height: 30px;
        outline:none;
        padding-left:10px;
        width:300px;
        border-top-left-radius: 4px;
        border-bottom-left-radius: 4px;
        border:1px solid #ccc;
    }
    button{
        line-height: 30px;
        background: #0089e1; 
        border:none;
        outline:none;
        width:80px;
        color:#fff;
        border-top-right-radius: 4px;
        border-bottom-right-radius: 4px;
    }
}
</style>

