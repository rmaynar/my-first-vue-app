<template>
    <div id="todo-list">
        {{titulo}}
    </div>
</template>
<script>
 export default{
     name: 'TodoList',
     data(){
         return{
             titulo:'Listado de tareas'
         }
     }
 }   
</script>