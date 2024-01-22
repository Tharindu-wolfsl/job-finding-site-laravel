<template>
    <div class="container">
        <header class="col-md-12 text-center">
            <h1 class="text-center">{{ job.name }}</h1>
            <p class="card-text text-muted">{{ job.company_name }}</p>
        </header>
        <section>
            <div class="col-md-10 mx-auto job-list">
                <div class="card mb-3  mx-auto">
                    <div class="row no-gutters">
                        <div class="col-md-4">
                            <img class :src="job.img" alt="...">
                        </div>
                        <div class="col-md-8">
                            <div class="card-body">
                                <p class="card-text">{{ job.description }}</p>
                                <p class="card-text"><small class="text-muted">{{ job.other }}</small></p>
                                <div class="input-group mb-3">
                                    <div class="custom-file">
                                        <input type="file" @change="handleFileUpload" class="custom-file-input">
                                        <label class="custom-file-label" for="inputGroupFile01">{{models.resume_file.name ? models.resume_file.name : 'Upload Resume.'}}</label>
                                    </div>
                                </div>
                                <button type="button" class="btn btn-primary" onclick="applyJob()">Submit</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>

<script>
export default {
    name: "JobPost",
    data() {
        return {
            search_text: '',
            job: {
                id: 1,
                img: '/assets/post.png',
                name: 'Job1',
                company_name: 'Company1',
                description: 'This is a wider card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.',
                other: 'Last updated 3 mins ago.'
            },
            models: {
                resume_file: {}
            }
        }
    },
    mounted() {
        this.getJobByID();
    },
    methods: {
        getJobByID() {

        },
        handleFileUpload(event) {
            console.log(event.target.files[0]);
            this.models.resume_file = event.target.files[0];
            // Access file properties (name, size, type) and perform actions
        },
        applyJob() {
            console.log(this.models.resume_file);
        },
    }
}
</script>

<style scoped>

</style>
