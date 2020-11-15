<template>


  <div class="q-pa-md" style="max-width: 100%">
    
    <q-list>
      <q-item
           @click="task.completed = !task.completed"
         tag="label"
          clickable
         v-ripple>
        <q-item-section side top>
          <q-checkbox 
          v-model="task.completed"           
          />
        </q-item-section>
        <q-item-section>
          <q-item-label :class="{'done' : task.completed}">{{ task.title }}</q-item-label>
        </q-item-section>

        <q-item-section class="dateDeleteBox" side top>
          <div v-if="task.completed" class="q-pa-sm">
             <q-icon clickable @click="deleteTodo(index)"  class="deleteIcon" name="delete" />
          </div>
          <div class="q-pa-sm">
            <q-item-label caption>Date</q-item-label>
            <q-item-label caption>5 min ago</q-item-label>
          </div>

        </q-item-section>
      </q-item>

    </q-list>
  </div>



</template>

<script>
//name: 'Todos'
export default {
  props :['task', 'index', 'tasks'] ,

  methods:{
    deleteTodo(index){
      this.tasks.splice(index, 1)
      console.log(index)
    }
  }

}
</script>

<style lang="scss">
  .done {
    text-decoration: line-through;
    color: #bbb ;
  }
  .deleteIcon {
    font-size: 28px;
  }
  .dateDeleteBox{
    display: -webkit-inline-box;
  }
</style>