<template>
    <div>
        <form @submit="addItem">
            <input type="Text" v-model="title" name="title" placeholder="Add Item">
            <input type="Submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
    import * as uuid from 'uuid';
    export default {
        name: "AddItem",
        data(){
            return {
                title: ''
            }
        },
        methods: {
            addItem(e) {
                e.preventDefault();
                const newItem = {
                    id: uuid.v4(),
                    title: this.title,
                    completed:false,
                    amount: 1
                }
                //Send up to parent
                this.$emit('add-item', newItem);
            }

        }
    }
</script>

<style scoped>
    form {
        display: flex;
    }
    input[type="Text"]{
        flex: 10;
        padding: 5px;
    }
    input[type="Submit"] {
        flex:2;
    }
</style>