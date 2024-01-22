<template>
    <div id="job-apply-modal" class="modal fade col-md-12 mx-auto" tabindex="-1" role="dialog"
         aria-labelledby="exampleModalCenterTitle" aria-hidden="true" data-backdrop="static" data-keyboard="false">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title">Apply Job</h5>
                    <button type="button" class="close" @click="close">
                        <span>&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                    <div class="input-group mb-3">
                        <div class="custom-file">
                            <input type="file" @change="handleFileUpload" class="custom-file-input">
                            <label class="custom-file-label"
                                   for="inputGroupFile01">{{
                                    models.resume_file.name ? models.resume_file.name : 'Upload Resume.'
                                }}</label>
                        </div>
                    </div>
                    <button type="button" class="btn btn-primary" @click="applyJob">Submit</button>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" @click="close">Close</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "JobApplyModal",
    data() {
        return {
            models: {
                resume_file: {}
            }
        }
    },
    methods: {
        close() {
            this.$emit("close"); // Emit `close` event to parent component
        },
        handleFileUpload(event) {
            console.log(event.target.files[0]);
            this.models.resume_file = event.target.files[0];
            // Access file properties (name, size, type) and perform actions
        },
        applyJob() {
            console.log(this.models.resume_file);
        },
    },
};
</script>

<style scoped>
.modal-body {
    text-align: center;
}
#job-apply-modal {
    margin-top: 10em;
}
</style>
