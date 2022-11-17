<template>
    <div>
        <form @submit.prevent="addItemAndClear(todo)">
            <input v-model="todo" type="text" /><button>Add</button>
        </form>
    </div>
</template>

<script>
import { ref } from "vue";
import { useTodoListStore } from '@/store/useTodoListStore'

export default {
    
    setup () {
        const todo = ref("");
        const store = useTodoListStore()

        function addItemAndClear(item) {
            if (!item) {
                return;
            }
            store.addTodo(item);
            todo.value = "";
        }
        return { todo, addItemAndClear, store };
    }
}
</script>

<style lang="scss" scoped>

</style>