<template>
    <div>
        <form @submit="addTodo">
            <input type="text" name="title" v-model="title" placeholder="add  to do..">
             <input type="submit" value="Submit" class="btn">


        </form>
    </div>
</template>
<script>
import uuid from 'uuid'
export default {
    name:"addToDo",
    data(){
        return{
        title:''
    }
    },
    methods: {
        addTodo(e){
            e.preventdefault();
            const newTodo={
                id: uuid.v4(),
                title: this.title,
                completed:false
            }
            // send it to parent
            this.$emit('add-todo', newTodo);
        }
    }
}
</script>
<style scoped>
form{
    display: flex;
}
input[type="text"]{
    flex: 10;
    padding:5px;

}
input[type="submit"]{
    flex: 2;
}
</style>


