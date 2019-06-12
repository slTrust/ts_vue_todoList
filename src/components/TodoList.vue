<template>
  <div>
    <ol class="todoList">
      <li v-for="(todoItem,index) in list" :key="index">
        <input type="checkbox" :checked="todoItem.status === 'done'" 
          @change="changeStatus(todoItem, $event)"
        >
        <span>{{todoItem.name}}</span>
        <button @click="deleteItem(todoItem)">del</button>
      </li>
    </ol>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Mixins } from 'vue-property-decorator';
import Todo from '../models/Todo';
@Component({
  props: {
    list: Array,
  },
})
export default class TodoList extends Vue {
  changeStatus(todoItem: Todo, e: Event) {
    let checked = (<HTMLInputElement>e.target).checked;
    this.$emit('updateTodo', todoItem, { status: checked ? 'done' : 'todo' });
  }
  deleteItem(todoItem:Todo){
    this.$emit('deleteTodoItem', todoItem);
  }
}
</script>
<style scoped lang="scss">
.todoList { 
    padding-top:10px;
    li{
        background: #eee;
        width:380px;
        margin:0 auto;
        margin-bottom:10px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        input{
            margin-left:10px;
        }
        button{
            line-height: 30px;
            background: #f55d5d; 
            border:none;
            outline:none;
            width:80px;
            color:#fff;
            border-top-right-radius: 4px;
            border-bottom-right-radius: 4px;
        }
    }
}
</style>
