<template>
    <v-list
      class="pt-2"
      flat
    >
    <draggable
        :list="tasks" 
        handle=".handle"
    >
        <task class="pt-0" v-for="(task) in tasks" 
            :key="task.id"
            :task="task"
        />
    </draggable>
    </v-list>
</template>

<script>
import draggable from "vuedraggable";
import Task from '@/components/Todo/Task.vue'
export default {
    components:{
        Task,
        draggable
    },
    computed: {
        tasks: {
            get(){
                return this.$store.getters.tasksFiltered
            },
            set(value){
                this.$$store.commit('setTasks', value)
            }
        }
    },
    methods:{
    
    }
}
</script>