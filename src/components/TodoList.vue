<template>
<div class="container">
<div class="input-add">
<input v-model="input" placeholder="Add task" /> <button @click="add()"> Add</button>
</div>
<List :list="todolist" @delete-task="deleteTask" @toggle-complete="toggleComplete"/>
</div>
</template>


<script>
import List from './List.vue'
export default {
    name:"TodoList",
    components:{
        List
    },
    data(){
        return{
            todolist:[],
            input:""
        }
    },
    methods:{
        add(){

            if(this.input){
                console.log("innn")
            this.todolist.push({task:this.input,completed:false})
            }
        },
        deleteTask(e){
            this.todolist.splice(e,1)
        },
        toggleComplete(e){
            if(this.todolist.length>0)
            this.todolist[e].completed = !(this.todolist[e]?.completed)
        }
    },
    emits:['delete-task','toggle-complete'],
    created(){
        this.todolist=[{
                task:"Today task",completed:false,

            },
            {
                task:"Tomorrow task",completed:true,
                
            }]
    }
}
</script>


<style >
.container{
    width:50%;
    display:flex;
    flex-direction:column;
    gap:10px;
    border:1px solid black;
    padding:10px;

}
input{
    padding:10px;
    border:1px dashed grey;

}

.input-add{
    display:flex;
    gap:10px;
}
button{
    border:1px dashed black;
    padding:10px 10px;
    background-color:transparent;
}
button:hover,input:hover,input:active{
    border-style: solid;
}
.input-add input{
    width:100%;
}
</style>