<template>
  <form 
    class="d-flex flex-column align-items-center justify-content-center"
    @submit.prevent='handleSubmit' 
  >
    <label for='newTask'>
      <h2>{{ setTitle }}</h2>
    </label>
    <div class="form-floating my-3 w-75">
      <input 
        class="form-control" 
        v-model.trim="title"
        type="text" 
        id="title" 
      >
      <label for="title" class="form-label">Title</label>
    </div>
    <div class="form-floating w-75 my-3">
      <textarea 
        class="form-control h-75" 
        v-model.trim="description"
        placeholder="Write a description here" 
        id="descriptionArea" 
      />
      <label for="descriptionArea">Description</label>
    </div>
    <button 
      type="submit" 
      class="btn btn-outline-primary my-3 px-3 w-25"
      data-bs-dismiss="modal" 
    >
      Save
    </button>
  </form>
</template>

<script>
export default {
  name: 'Form',
  data() {
    return {
      title: '',
      description: ''
    }
  },
  props: {
    isEditing: Boolean,
    item: Object
  },
  emits: ['addTask', 'editTask'],
  methods: {
    handleSubmit() {
      const item = { 
        ...this.item, 
        title: this.title, 
        description: this.description 
      }

      if(this.isEditing) {
        this.$emit('editTask', item)
      } else {
        this.$emit('addTask', item)
      }
      this.title = ''
      this.description = ''
    }
  },
  computed: {
    setTitle() {
        if(this.isEditing) return 'Edit To-Do'
        return 'Add To-Do'
    }
  },
  mounted() {
    if(!this.isEditing) return

    this.title = this.item.title,
    this.description = this.item.description
  }
}
</script>

<style scoped>


</style>
