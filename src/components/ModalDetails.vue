<template>
    <div class="modal fade" id="detailsModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-dialog-centered">
            <div class="modal-content">
                <div class="modal-header">
                    <h3 class="modal-title" id="exampleModalLabel">To-Do</h3>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div 
                    v-if="mode === 'details'"
                    class="modal-body d-flex flex-column" 
                >
                    <h4>
                        {{ selectedItem.title }}
                    </h4>
                    <hr class="w-75 align-self-center">
                    <p>
                        {{ selectedItem.description }}
                    </p>
                </div>
                <Form 
                    v-if="mode === 'edit'"
                    :isEditing='true'
                    :item="selectedItem"
                    @editTask="editTask"
                />
            </div>
        </div>
    </div>
</template>

<script>
import Form from './Form.vue';
export default {
    name: 'ModalDetails',
    components: {
        Form
    },
    props: {
        mode: String,
        selectedItem: Object
    },
    emits: ['editTask'],
    methods: {
        editTask(item) {
            this.$emit('editTask', item)
        }
    }
}

</script>

<style>


</style>