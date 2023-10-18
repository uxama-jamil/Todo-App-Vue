<template>

<div v-for="(t, i) in list" :key="i" :class="['list-container',t.completed ? 'completed' : '']"  @click="$emit('toggle-complete',i)">

    <span>{{t.task}}</span><button @click="$emit('delete-task',i)">Delete</button>

</div>

</template>


<script>
export default {
    name:"ListComp",
    props:['list']

}
</script>


<style scoped>
.list-container{
    display:flex;
    gap:10px;
    justify-content:space-between;
    align-items: center;
    border:1px dashed green;
    width:50%;
    padding:10px;
    cursor:pointer;
}
.completed{
    border-style:solid;
}
button{
    border:1px dashed black;
    padding:10px 10px;
    background-color:transparent;
}
</style>