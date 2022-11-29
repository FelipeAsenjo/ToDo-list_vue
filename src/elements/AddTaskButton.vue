<template>
    <button 
        type="button" 
        class="btn btn-outline-dark py-2" 
        data-bs-toggle="modal" 
        data-bs-target="#formModal"
        @click="$emit('resetSelectedItem')"
    >
            Add To-Do
    </button>
</template>

<script>
export default {
    name: 'AddTaskButton',
    emits: ['resetSelectedItem']
}

</script>

<style></style>