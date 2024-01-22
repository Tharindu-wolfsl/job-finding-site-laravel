<template>
    <main>
        <!-- Hero Area Start-->
        <div class="slider-area ">
            <div class="single-slider section-overly slider-height2 d-flex align-items-center" data-background="/img/hero/about.jpg">
                <div class="container">
                    <div class="row">
                        <div class="col-xl-12">
                            <div class="hero-cap text-center">
                                <h2>{{job.subject}}</h2>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="job-post-company pt-120 pb-120">
            <div class="container">
                <div class="row justify-content-between">
                    <!-- Left Content -->
                    <div class="col-xl-7 col-lg-8">
                        <!-- job single -->
                        <div class="single-job-items mb-50">
                            <div class="job-items">
                                <div class="company-img company-img-details">
                                    <a href="#"><img src="/img/icon/job-list1.png" alt=""></a>
                                </div>
                                <div class="job-tittle">
                                    <a href="#">
                                        <h4>{{job.subject}}</h4>
                                    </a>
                                    <ul>
                                        <li>{{job.company_name}}</li>
                                        <li><i class="fas fa-map-marker-alt"></i>{{job.company_address}}</li>
                                        <li>{{job.company_salary_range}}</li>
                                    </ul>
                                </div>
                            </div>
                        </div>
                        <!-- job single End -->

                        <div class="job-post-details">
                            <div class="post-details1 mb-50">
                                <!-- Small Section Tittle -->
                                <div class="small-section-tittle">
                                    <h4>Job Description</h4>
                                </div>
                                <p>It is a long established fact that a reader will beff distracted by vbthe creadable content of a page when looking at its layout. The pointf of using Lorem Ipsum is that it has ahf mcore or-lgess normal distribution of letters, as opposed to using, Content here content here making it look like readable.</p>
                            </div>
                            <div class="post-details2  mb-50">
                                <!-- Small Section Tittle -->
                                <div class="small-section-tittle">
                                    <h4>Required Knowledge, Skills, and Abilities</h4>
                                </div>
                                <ul>
                                    <li>System Software Development</li>
                                    <li>Mobile Applicationin iOS/Android/Tizen or other platform</li>
                                    <li>Research and code , libraries, APIs and frameworks</li>
                                    <li>Strong knowledge on software development life cycle</li>
                                    <li>Strong problem solving and debugging skills</li>
                                </ul>
                            </div>
                            <div class="post-details2  mb-50">
                                <!-- Small Section Tittle -->
                                <div class="small-section-tittle">
                                    <h4>Education + Experience</h4>
                                </div>
                                <ul>
                                    <li>3 or more years of professional design experience</li>
                                    <li>Direct response email experience</li>
                                    <li>Ecommerce website design experience</li>
                                    <li>Familiarity with mobile and web apps preferred</li>
                                    <li>Experience using Invision a plus</li>
                                </ul>
                            </div>
                        </div>

                    </div>
                    <!-- Right Content -->
                    <div class="col-xl-4 col-lg-4">
                        <div class="post-details3  mb-50">
                            <!-- Small Section Tittle -->
                            <div class="small-section-tittle">
                                <h4>Job Overview</h4>
                            </div>
                            <ul>
                                <li>Posted date : <span>12 Aug 2019</span></li>
                                <li>Location : <span>New York</span></li>
                                <li>Vacancy : <span>02</span></li>
                                <li>Job nature : <span>Full time</span></li>
                                <li>Salary :  <span>$7,800 yearly</span></li>
                                <li>Application date : <span>12 Sep 2020</span></li>
                            </ul>
                            <div class="apply-btn2">
                                <button class="btn btn-primary" @click="showModal">Apply Now</button>
                            </div>
                        </div>
                        <div class="post-details4  mb-50">
                            <!-- Small Section Tittle -->
                            <div class="small-section-tittle">
                                <h4>Company Information</h4>
                            </div>
                            <span>Colorlib</span>
                            <p>It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout.</p>
                            <ul>
                                <li>Name: <span>Colorlib </span></li>
                                <li>Web : <span> colorlib.com</span></li>
                                <li>Email: <span>carrier.colorlib@gmail.com</span></li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <JobApplyModal @close="hideModal" ></JobApplyModal>
    </main>
</template>

<script>
import JobApplyModal from "./JobApplyModal";
export default {
    name: "JobPost",
    components: {JobApplyModal},
    data() {
        return {
            search_text: '',
            job: {
                id:1,
                img:'img/icon/job-list1.png',
                subject:'Digital Marketer',
                company_name:'Creative Agency',
                company_address:'Athens, Greece',
                company_salary_range:'$3500 - $4000',
                description:'This is a wider card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.',
                job_type:'Full Time',
                job_posted:'7 hours ago.'
            }
        }
    },
    mounted() {
        this.getJobByID();
    },
    methods: {
        getJobByID() {

        },
        hideModal() {
            $("#job-apply-modal").modal('hide');
        },
        showModal() {
            $("#job-apply-modal").modal('show');
        }
    }
}
</script>

<style scoped>

</style>
