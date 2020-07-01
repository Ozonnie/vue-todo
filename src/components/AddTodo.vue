<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="title">
        <button type="submit" class="submit-btn">Create</button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            title: ''
        }
    },
    methods: {
        onSubmit() {
            if (this.title.trim()) {
                const newTodo = {
                    id: Date.now(),
                    title: this.title,
                    completed: false
                }

                this.$emit('add-todo', newTodo)
                this.title = ''
            }
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
        justify-content: center;
        margin: 25px 0;

    }
    input {
        width: 300px;
    }
    .submit-btn {
        background: green;
        color: #fff;
        border: none;
        border-radius: 3px;
        padding: 10px 45px;
        font-size: 14px;
        margin-left: 15px;
        margin-right: 15px;
        cursor: pointer;
    }

    .submit-btn:hover {
        background: rgb(2, 100, 2);
    }
</style>