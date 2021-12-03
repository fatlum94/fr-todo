<template>
    <v-text-field
      v-model="newTaskTitle"
      @keyup.enter="addTask"
      outlined
      label="Add New Todo"
      class="pa-3"
      hide-details
      clearable
    >
      <template v-slot:append>
        <v-icon @click="addTask" color="primary" :disabled="newTaskTitleIvalid">
          mdi-plus
        </v-icon>
      </template>
    </v-text-field>
</template>
<script>
export default({
    data() {
      return {
        newTaskTitle: ''
      }
    },
    computed:{
      newTaskTitleIvalid(){
        return !this.newTaskTitle
      }
    },
    methods:{
      addTask(){
        if(!this.newTaskTitleIvalid){
          // this.$store.commit('addTask', this.newTaskTitle) u can call diret a mutations with commit
          this.$store.dispatch('addTask', this.newTaskTitle)
          this.newTaskTitle = ''
        }
      }
    }
})
</script>
