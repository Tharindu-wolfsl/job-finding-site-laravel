<template>
    <div>
        <main>
            <!-- Hero Area Start-->
            <div class="slider-area ">
                <div class="single-slider section-overly slider-height2 d-flex align-items-center"
                     data-background="/img/hero/about.jpg">
                    <div class="container">
                        <div class="row">
                            <div class="col-xl-12">
                                <div class="hero-cap text-center">
                                    <h2>Get your job</h2>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="job-listing-area pt-120 pb-120">
                <div class="container">
                    <div class="col-xl-10 col-lg-10 col-md-8 mx-auto">
                        <!-- Featured_job_start -->
                        <section class="featured-job-area">
                            <div class="container">
                                <div class="job-search col-md-8 mx-auto">
                                    <div class="input-group mb-3">
                                        <input type="text" class="form-control" placeholder="Search jobs here"
                                               aria-label="Recipient's username" aria-describedby="basic-addon2"
                                               v-modal="search_text">
                                        <div class="input-group-append">
                                            <button class="btn btn-outline-secondary" type="button" @click="getJobList">
                                                Search
                                            </button>
                                        </div>
                                    </div>
                                </div>
                                <!-- Count of Job list Start -->
                                <div class="row">
                                    <div class="col-lg-12">
                                        <div class="count-job mb-35">
                                            <span>{{ models.jobs.length + ' Jobs found' }}</span>
                                            <!-- Select job items start -->
                                            <div class="select-job-items">
                                            </div>
                                            <!--  Select job items End-->
                                        </div>
                                    </div>
                                </div>
                                <div class="job-list-container" v-if="models.jobs.length != 0">
                                    <div v-for="job in models.jobs">
                                        <router-link :to="'/job/'+job.id">
                                            <div class="single-job-items mb-30">
                                                <div class="job-items">
                                                    <div class="company-img">
                                                        <a href="#"><img :src="job.img" alt=""></a>
                                                    </div>
                                                    <div class="job-tittle job-tittle2">
                                                        <a href="#">
                                                            <h4>{{ job.subject }}</h4>
                                                        </a>
                                                        <ul>
                                                            <li>{{ job.company_name }}</li>
                                                            <li><i
                                                                class="fas fa-map-marker-alt"></i>{{
                                                                    job.company_address
                                                                }}
                                                            </li>
                                                            <li>{{ job.company_salary_range }}</li>
                                                        </ul>
                                                    </div>
                                                </div>
                                                <div class="items-link items-link2 f-right">
                                                    <a href="job_details.html">{{ job.job_type }}</a>
                                                    <span>{{ job.job_posted }}</span>
                                                </div>
                                            </div>
                                        </router-link>
                                    </div>
                                </div>
                                <div v-else>
                                    <span>No jobs found</span>
                                </div>
                            </div>
                        </section>
                    </div>
                </div>
            </div>
        </main>
    </div>
</template>

<script>
export default {
    name: "Home"
    ,
    data() {
        return {
            search_text: '',
            models: {
                jobs: [{
                    id: 1,
                    img: 'img/icon/job-list1.png',
                    subject: 'Digital Marketer',
                    company_name: 'Creative Agency',
                    company_address: 'Athens, Greece',
                    company_salary_range: '$3500 - $4000',
                    description: 'This is a wider card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.',
                    job_type: 'Full Time',
                    job_posted: '7 hours ago.'
                }, {
                    id: 2,
                    img: 'img/icon/job-list2.png',
                    subject: 'Software Engineer',
                    company_name: 'Creative Agency',
                    company_address: 'Athens, Greece',
                    company_salary_range: '$3500 - $4000',
                    description: 'This is a wider card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.',
                    job_type: 'Full Time',
                    job_posted: '7 hours ago.'
                }, {
                    id: 3,
                    img: 'img/icon/job-list3.png',
                    subject: 'Graphic Designer',
                    company_name: 'Creative Agency',
                    company_address: 'Athens, Greece',
                    company_salary_range: '$3500 - $4000',
                    description: 'This is a wider card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.',
                    job_type: 'Full Time',
                    job_posted: '7 hours ago.'
                }, {
                    id: 3,
                    img: 'img/icon/job-list3.png',
                    subject: 'Graphic Designer',
                    company_name: 'Creative Agency',
                    company_address: 'Athens, Greece',
                    company_salary_range: '$3500 - $4000',
                    description: 'This is a wider card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.',
                    job_type: 'Full Time',
                    job_posted: '7 hours ago.'
                }, {
                    id: 3,
                    img: 'img/icon/job-list3.png',
                    subject: 'Graphic Designer',
                    company_name: 'Creative Agency',
                    company_address: 'Athens, Greece',
                    company_salary_range: '$3500 - $4000',
                    description: 'This is a wider card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.',
                    job_type: 'Full Time',
                    job_posted: '7 hours ago.'
                }, {
                    id: 3,
                    img: 'img/icon/job-list3.png',
                    subject: 'Graphic Designer',
                    company_name: 'Creative Agency',
                    company_address: 'Athens, Greece',
                    company_salary_range: '$3500 - $4000',
                    description: 'This is a wider card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.',
                    job_type: 'Full Time',
                    job_posted: '7 hours ago.'
                },]
            },
        }
    },
    mounted() {
        this.getJobList();
    },
    methods: {
        getJobList() {

        }
    }
}
</script>

<style scoped>
.job-list-container {
    max-height: 80vh;
    overflow-y: scroll;
}
</style>
