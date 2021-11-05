<template>
  <form @submit.prevent='addTask'>
    <label for='newTask'>Tarea</label>
    <input v-model='input' type='text' placeholder='Ingresa nueva tarea'/>
    <input type='submit' value=' Añade ' />
  </form>
  <ul>
    <HelloWorld v-for='( task, idx ) in tasks' 
      :key='idx' :id='task.id' :title='task.value' 
      @removeTask='remove'/>
  </ul>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {
      input: '',
      tasks: []
    }
  },
  methods: {
    addTask() {
      this.tasks.push({
        id: new Date().toISOString(),
        value: this.input
      })

      this.input = ''
    },
    remove( id ) {
      this.tasks.forEach( (t, i) => {
        if( Object.values(t).indexOf(id) > -1 ) {
          this.tasks.splice(i, 1)
        }

        return
      } )
    }
  }
}
</script>

<style>
#app {
  margin: 10vh 0;
  font-size: 1.4rem;
  text-align: center;
  font-weight: 600;
}

#app input {
  margin: 0 1rem;
  border-radius: 10px;
}

</style>
