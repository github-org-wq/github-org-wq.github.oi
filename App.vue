
<template>

  <div id="app">
     <h1 class="ui dividing centered header">Vue.js Todo App</h1>
    <div class='ui three column centered grid'>
      <div class='column'>
        <!-- 为了不让原本的HelloWorld组件以及图片影响其他组件的显示，在template将其注释或者删除 -->
    <!--<img src="./assets/logo.png"
    //3.在template部分用声明的组件名称作为标签名称来使用组件 > -->
    <TodoList v-bind:todos="todos" ></TodoList>
     <create-todo v-on:create-todo="createTodo"></create-todo>
      </div>
    </div>
  </div>
</template>

<script>
//1.导入要使用的组件
import sweetalert from 'sweetalert';
import TodoList from './components/TodoList';
import CreateTodo from './components/CreateTodo';


//2.在Vue实例中components属性中声明组件
export default {
  name: 'App',
  components: {
   TodoList,
    CreateTodo,
  },
  //利用dat属性来定义todos变量
  data(){
    return {
      //todos变量为一个数组，用来储存备忘录数据，数组中每个元素即每件事是一个对象，具有标题，项目和完成（指示待办事项是否完整）三个属性
      todos:[
        {
          title:"Todo A",
          project:"Project A",
          done:false
        },
        {
          title:"Todo B",
          project:"Project B",
          done:true
        },
        {
          title:"Todo C",
          project:"Project C",
          done:false
        },
        {
          title:"Todo D",
          project:"Project D",
          done:false
        }
      ]
    };
  },
   methods: {
    createTodo(newTodo) {
      this.todos.push(newTodo);
      sweetalert('Success!', 'To-Do created!', 'success');
    },
  },
};
</script>

<style>

</style>
