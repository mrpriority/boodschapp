<template>
    <div class="todo-item" v-bind:class="{'is-complete':item.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete(item.id)" >
            {{item.title}}
            <input @click="$emit('minAmount',item.id)" type="button" value="-" class="btn">
            {{item.amount}}
            <input @click="$emit('plusAmount',item.id)" type="button" value="+" class="btn">
            <button @click="$emit('delItem', item.id)" class="del">x</button>
            <input @click="$emit('minIndex',item.id)" type="button" value="🠋" class="move">
            <input @click="$emit('plusIndex',item.id)" type="button" value="🠉" class="move2">

        </p>
    </div>
</template>

<script>
    export default {
        name: "ItemTodo",
        props: ["item"],
        methods: {
            markComplete(id) {
                this.item.completed = !this.item.completed;
                this.$emit('markComplete', id);
            }
        }
    }
</script>

<style scoped>
 .todo-item {
     background: #f4f4f4;
     padding: 10px;
     border-bottom: 1px #ccc dotted;
 }
    .is-complete{
        text-decoration: line-through;
        color: #777777;
    }
    .del {
        background: #ff0000;
        color: #fff;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
    .move{
       display: inline-block;
       border: none;
       background: #555;
       color: #fff;
       padding: 7px;
       cursor: pointer;
       margin-right: 50%;
        float: right;
    }
 .move2{
     display: inline-block;
     border: none;
     background: #555;
     color: #fff;
     padding: 7px;
     cursor: pointer;
     float: right;
 }
</style>