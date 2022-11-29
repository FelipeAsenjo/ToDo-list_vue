<template>
    <li class="d-flex justify-content-center"> 
      <button 
        @click='$emit("select", task, "details")' 
        class="card w-100 mx-3"
        data-bs-toggle="modal" 
        data-bs-target="#detailsModal"
      >
          <div class="card-body">
            {{ task.title }} 
          </div>
      </button>
      <button 
        @click='$emit("select", task, "edit")' 
        type="button" 
        class="btn btn-warning mx-1"
        data-bs-toggle="modal" 
        data-bs-target="#detailsModal"
      >
        Edit
      </button>
      <button 
        @click='$emit("removeTask", task.id)' 
        type="button" 
        class="btn btn-danger mx-1"
      >
        Delete
      </button>
    </li>

</template>

<script>
export default {
  name: 'TaskItem',
  props: {
    task: Object,
  },
  emits: ['removeTask', 'select']
}
</script>

<style scoped>
li {
  width: 100%;
  list-style: none;
}

.card-body:hover {
  cursor: pointer;
}

</style>
