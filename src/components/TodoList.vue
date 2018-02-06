<template>
    <div id="todo-list">
        <h2>{{titulo}}</h2>
        <ul class="listado">
            <li v-for="tarea in tareas">
                <el-checkbox v-model="tarea.checked">{{tarea.nombre}}</el-checkbox><a class="el-icon-delete" v-on:click="eliminarTarea(tarea)"></a>
            </li>
        </ul>
        <el-form ref="form" :model="form" label-width="180px">
            <el-form-item label="Insert new task">
                <el-input class="input-class" v-model="form.nuevatarea.nombre" placeholder="..task description" size="40" ></el-input>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="anadir">Insert</el-button>
                <el-button @click="eliminarTodas">Delete</el-button>
            </el-form-item>
        </el-form>
    </div>
</template>
<script>
 export default{
     name: 'TodoList',
     data(){
         return {
             titulo:"To-do list",
             form:{
                 nuevatarea:{'nombre':''}
             },
             tareas:
                 [
                     {'nombre':'tarea1',checked:false},
                     {'nombre':'tarea2',checked:false},
                     {'nombre':'tarea3',checked:false},
                     {'nombre':'tarea4',checked:false},
                     {'nombre':'tarea5',checked:false}
                 ]
             
         }
     },
     methods:{
         anadir(){
             var tarea = {'nombre':this.$data.form.nuevatarea.nombre};
             if(tarea.nombre!=""){
                 tarea.checked=false;
                 this.$data.tareas.push(tarea);
                alert("Task successfully saved!");
             }else{
                 alert("Task is blank")
             }
             
         },
         eliminarTodas(){
             for(var i = 0; i<this.$data.tareas.length;i++){
                 if(this.$data.tareas[i].checked){
                     this.$data.tareas.splice(i, 1);
                 }
             }
         },
         eliminarTarea(tarea){
             this.$data.tareas.splice(this.$data.tareas.indexOf(tarea), 1);
         }
     }
     
 }   
</script>

<style>
 .nuevatareaLbl{
     margin-right:1em;
 }   
 #todo-list{
     text-align:left;
 }
 .listado{
     list-style: none;
 }
 .input-class{
     width:200px;
 }
</style>