<template>
    <div id="todo-list">
        <h2>{{titulo}}</h2>
    </div>
</template>
<script>
 export default{
     name: 'TodoList',
     data(){
         return {
             titulo:"To-do list"
         }
     }
     
 }   
</script>