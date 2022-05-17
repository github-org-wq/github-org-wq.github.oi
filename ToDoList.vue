<template >
<div>
    <p class="tasks">Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p class="tasks">Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="todo in todos" :todo.sync="todo" key="index"></todo>
  </div>
  
</template>

<script type="text/javascript">
//1.导入组件
import todo from "../components/Todo.vue";
import sweetalert from "sweetalert";
//2.在components属性中声明组件
export default {
  props: ["todos"],
  components: { todo },

//调用data函数
  data() {
    return {};
  },
  methods: {
    deleteTodo(todo) {
      // const todoIndex = this.todos.indexOf(todo);
      // this.todos.splice(todoIndex, 1);
      sweetalert(
        {
          title: "Are you sure?",
          text: "This To-Do will be permanently deleted!",
          type: "warning",
          buttons: true,
          confirmButtonColor: "#DD6B55",
          confirmButtonText: "Yes, delete it!",
          closeOnConfirm: false
        }
        // () => {
        //   const todoIndex = this.todos.indexOf(todo);
        //   this.todos.splice(todoIndex, 1);
        //   sweetalert("Deleted!", "Your To-Do has been deleted.", "success");
      ).then(willDelete => {
        if (willDelete) {
          const todoIndex = this.todos.indexOf(todo);
          this.todos.splice(todoIndex, 1);
          sweetalert("Deleted!", "Your To-Do has been deleted.", "success");
        }
      });
    },
    completeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = true;
      sweetalert("Success!", "To-Do completed!", "success");
    }
  }
};
</script>

<style>
</style>