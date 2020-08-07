<template>
    <div class="todo-container">
        <div class="todo-wrap">
            <ToDoHeader :addTodo="addTodo"/>
            <ToDoList :todos="todos" :deleteTodo="deleteTodo"/>
            <ToDoFooter :todos="todos" :deleteCompleteTodos="deleteCompleteTodos" :selectAllTodos="selectAllTodos"/>
        </div>
    </div>
</template>

<script>
    import ToDoHeader from './components/ToDoHeader.vue'
    import ToDoList from "@/components/ToDoList.vue";
    import ToDoFooter from "@/components/ToDoFooter.vue";
    export default {

        data(){
          return{
              todos:[
                  {title:'吃放',complete:false},
                  {title:'睡觉',complete:true},
                  {title:'coding',complete:false}
              ]
            }
        },
        methods:{
            addTodo(todo){
                this.todos.unshift(todo)
            },
            deleteTodo(index){
                this.todos.splice(index,1)
            },
            deleteCompleteTodos(){
                this.todos = this.todos.filter(todo => !todo.complete)
            },
            selectAllTodos(check){
                this.todos.forEach(todo => todo.complete=check)
            }
        },
        components:{
            ToDoHeader,
            ToDoFooter,
            ToDoList
        },

    }
</script>

<style>
    .todo-container {
        width: 600px;
        margin: 0 auto;
    }
    .todo-container .todo-wrap {
        padding: 10px;
        border: 1px solid #ddd;
        border-radius: 5px;
    }
</style>