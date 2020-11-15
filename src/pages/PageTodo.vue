<template>
    <div class="q-pa-md" style="max-width: 100%">

    <div>
     <q-input 
     v-model="newTask"
     @keyup.enter="addtask()" 
     placeholder="Add Task" 
     counter maxlength="12" 
     :dense="dense">
        <template v-slot:append>
          <q-btn @click="addtask()" round dense flat icon="add" />
        </template>
      </q-input>
    </div>
      <Todos
      v-for="(task, index) in tasks"
      :task="task"  
      :tasks="tasks" 
      :key="task.title"
      :index="index"
      >  
      </Todos>
    </div>
</template>

<script>
import Todos from './Todos.vue'

export default {

  data() {

    return {
        newTask : "",
        tasks: [    
          {
            title: "Get Phone",
            completed: true
          },
          {
            title: "Use Phone",
            completed: true
          },
          {
            title: "Break Phone",
            completed: false
          }
         ]
       
      }
    },

    methods:{
      addtask(){
        this.tasks.push({
          title: this.newTask,
          completed:false
        })
      }
    },

     components: {
         Todos
    }
 
}
</script>

<style>

</style>