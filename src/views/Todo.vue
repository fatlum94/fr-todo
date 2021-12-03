<template>
  <div class="home">
    <field-add-task />

    <list-tasks 
      v-if="$store.state.tasks.length"
    />

    <no-task  v-else />

    <button-done-sorting 
      v-if="$store.state.sorting"
    />
  </div>
</template>

<script>
import FieldAddTask from '@/components/Todo/FieldAddTask.vue'
import ListTasks from '@/components/Todo/ListTasks.vue'
import NoTask from '@/components/Todo/NoTask.vue'
import ButtonDoneSorting from '@/components/Todo/ButtonDoneSorting.vue'
  export default {
    name: 'ToDo',
    data() {
      return {
      }
    },
    components: {
      FieldAddTask,
      ListTasks,
      NoTask,
      ButtonDoneSorting
      // 'list-tasks': require('@/components/Todo/ListTasks.vue').default  you can do so 
    }
  }
</script>


