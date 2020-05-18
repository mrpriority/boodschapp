<template>
    <div>
        <div v-bind:key="item.id" v-for="item in items">
            <ItemTodo v-bind:item="item" v-on:delItem="$emit('delItem', item.id)" v-on:plusAmount="$emit('plusAmount', item.id)" v-on:minAmount="$emit('minAmount', item.id)" v-on:markComplete="$emit('markComplete', item.id)" v-on:plusIndex="$emit('plusIndex', item.id)" v-on:minIndex="$emit('minIndex', item.id)"/>
        </div>
    </div>
</template>

<script>
    import ItemTodo from "@/components/ItemTodo";
    export default {
        name: "items",
        components:{
            ItemTodo
        },
        props: ["items"]

    }
</script>

<style scoped>

</style>