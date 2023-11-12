<template>
    <main>
        <h1>Lista de Tarefas</h1>
        <p>Criar lista de Tarefas</p>

        <div class="create-new">
            <input type="text" v-model="newTask" placeholder="Adicionar Nova Tarefa" @keypress.enter="addTask" />
            <button @click="addTask">Adicionar</button>
        </div>

        <div class="tasks">
            <Task v-for="(task, i) in $store.state.tasks" :key="i" :task="task" />
        </div>

    </main>
</template>
<script>
export default {
    data() {
        return {
            newTask: ''
        }
    },
    methods: {
        addTask() {
            if (this.newTask) {
                this.$store.commit('ADD_TASK', this.newTask);
                this.newTask = '';
            }
        }
    }
}
</script>
