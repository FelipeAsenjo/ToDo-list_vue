<template class="container-fluid">
  <main class="container vh-100 py-5">
    <h1 class="primary">To-DoEr</h1>
    <section class="mt-5">
      <AddTaskButton @resetSelectedItem='resetSelectedItem' /> 
      <ul>
        <TaskItem 
          class="my-4"
          v-for='( task ) in tasks' 
          :key='task.id' 
          :task='task' 
          @select="setSelectedItem"
          @removeTask='removeTask'
        />
      </ul>
    </section>
    <ModalForm @addTask='addTask' />
    <ModalDetails 
      :mode="mode" 
      :selectedItem="selectedItem" 
      @editTask="editTask"
    />
  </main>
</template>

<script>
import TaskItem from './components/TaskItem.vue'
import ModalForm from './components/ModalForm.vue'
import ModalDetails from './components/ModalDetails.vue'
import AddTaskButton from './elements/AddTaskButton.vue'

export default {
  name: 'App',
  components: {
    TaskItem,
    ModalForm,
    ModalDetails,
    AddTaskButton
  },
  data() {
    return {
      tasks: [],
      selectedItem: null,
      mode: null
    }
  },
  methods: {
    addTask(item) {
      this.tasks.push({
        id: new Date().toISOString(),
        ...item,
      })
    },
    editTask(item) {
      const task = this.findTask(item.id)
      const itemToSave = { ...task, ...item}
      this.tasks.forEach((task, idx) => {
        if(task.id === itemToSave.id) {
          this.tasks.splice(idx, 1, itemToSave)
        }
      })
    },
    removeTask( id ) {
      const itemToDelete = this.findTask(id)
      this.tasks.forEach((task, idx) => {
        if( task.id === itemToDelete.id ) {
          this.tasks.splice(idx, 1)
        }
      })
    },
    setSelectedItem(task, mode) {
      this.selectedItem = task
      this.mode = mode
    },
    resetSelectedItem() {
      this.selectedItem = null
      this.mode = null
    },
    findTask(id) {
      return Object.values(this.tasks).filter(task => task.id === id)[0]
    }
  }
}
</script>

<style>
body {
  background: linear-gradient(135deg, #e66465, #9198e5);
  font-size: 1.4rem;
}
#app {
  text-align: center;
}

</style>
