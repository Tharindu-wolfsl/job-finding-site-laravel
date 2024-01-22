<template>
    <div class="container">
        <pre>{{models}}</pre>
        <header class="col-md-12 my-5">
            <h1 class="text-center d-block mx-auto">My job Hub</h1>
        </header>
        <section class="col-md-12">
            <div class="col-md-8 mx-auto search-box">
                <div class="input-group mb-3">
                    <input type="text" class="form-control" placeholder="Search job"  aria-describedby="basic-addon" v-model="models.search_text" onclick="getJobList()" >
                    <div class="input-group-append">
                        <span class="input-group-text" id="basic-addon2">Search</span>
                    </div>
                </div>
            </div>
            <div class="col-md-10 mx-auto job-list">
                <div v-for="job in models.jobs"  class="card mb-3  mx-auto" style="max-width: 540px;">
                    <div class="row no-gutters">
                        <div class="col-md-4">
                            <img class :src="job.img" alt="...">
                        </div>
                        <div class="col-md-8">
                            <div class="card-body">
                                <h5 class="card-title">{{ job.name }}</h5>
                                <p class="card-text text-muted">{{job.company_name}}</p>
                                <p class="card-text">{{ job.description}}</p>
                                <p class="card-text"><small class="text-muted">job.other</small></p>
                                <router-link :to="'job/'+job.id">
                                    <button class="btn btn-primary">Apply</button>
                                </router-link>
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
    name: "Home"
    ,
    data(){
        return{
            models:{
                search_text:'',
                jobs: [{
                    id:1,
                    img:'/assets/post.png',
                    name:'Job1',
                    company_name:'Company1',
                    description:'This is a wider card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.',
                    other:'Last updated 3 mins ago.'
                },{
                    id:2,
                    img:'/assets/post.png',
                    name:'Job2',
                    company_name:'Company2',
                    description:'This is a wider card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.',
                    other:'Last updated 3 mins ago.'
                },{
                    id:3,
                    img:'/assets/post.png',
                    name:'Job3',
                    company_name:'Company3',
                    description:'This is a wider card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.',
                    other:'Last updated 3 mins ago.'
                },]
            },

        }
    },
    mounted() {
        this.getJobList();
    },
    methods:{
        getJobList(){

        }
    }
}
</script>

<style scoped>

</style>
