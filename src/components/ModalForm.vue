<template>
    <div class="modal fade" id="formModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-dialog-centered">
            <div class="modal-content">
                <div class="modal-header">
                    <h3 class="modal-title" id="exampleModalLabel">
                        Add To-Do
                    </h3>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body d-flex flex-column">
                    <Form @addTask="addTask" />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Form from './Form.vue'

export default {
    name: 'ModalForm',
    components: {
        Form
    },
    props: {
        mode: String,
        selectedItem: Object
    },
    emits: ['addTask'],
    methods: {
        addTask(item) {
            this.$emit('addTask', item)
        }
    }
}

</script>

<style>


</style>