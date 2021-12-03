<template>
     <div>
      <v-list-item 
        @click="doneTask(task.id)"
        :class="{'blue lighten-5': task.done}"
        :ripple="false"
        class="white"
      >
          <template v-slot:default>
            <v-list-item-action>
              <v-checkbox
                :input-value="task.done"
                color="primary"
              ></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title :class="{'text-decoration-line-through': task.done}">{{task.title}}</v-list-item-title>
            </v-list-item-content>

            <v-list-item-action v-if="task.dueDate">
                <v-list-item-action-text>
                  <v-icon small>
                    mdi-calendar
                  </v-icon>
                  {{ task.dueDate | niceDate}}
                </v-list-item-action-text>
            </v-list-item-action>

            <v-list-item-action>
            <!-- <v-btn 
              @click.stop="dialogs.delete = true"
              icon>
              <v-icon color="primary lighten-1">mdi-delete</v-icon>
            </v-btn> -->
            <task-menu :task="task" />
          </v-list-item-action>

          <v-list-item-action v-if="$store.state.sorting">
              <v-btn
                color="primary"
                class="handle"
                icon
              >
                  <v-icon>mdi-drag-horizontal-variant</v-icon>
              </v-btn>
          </v-list-item-action>
          </template>
        </v-list-item>
        <v-divider></v-divider>
      </div>
</template>
<script>
import { format } from 'date-fns';
export default {
    data(){
        return{
            dialogs: {
                delete: false
            }
        }
    },
    components:{
        'dialog-delete': require('@/components/Dialogs/DialogDelete.vue').default,
        'task-menu': require('@/components/Todo/TaskMenu.vue').default
    },
    props: ['task'],
    filters:{
      niceDate(value) {
        return format(new Date(value), 'MMM d')
      }
    },
    methods:{
      doneTask(id){
         this.$store.commit('doneTask', id)
      },
      deleteTask(id){
        this.$store.dispatch('deleteTask', id)
      }
    }
}
</script>
<style lang="sass">
  .sorttable-ghost
    opacity: 0
  .sortable-drag
    box-shadow: 0 0 10px rgba(0,0,0,0.3)
</style>