<template>
    <div class="app">
        <header>
            <!-- Header Start -->
            <div class="header-area header-transparrent">
                <div class="headder-top header-sticky">
                    <div class="container">
                        <div class="row align-items-center">
                            <div class="col-lg-3 col-md-2">
                                <!-- Logo -->
                                <router-link :to="'/'">
                                    <div class="logo">
                                        <div><img src="/img/logo/logo.png" alt=""></div>
                                    </div>
                                </router-link>
                            </div>
                            <div class="col-lg-9 col-md-9">
                                <div class="menu-wrapper">
                                    <!-- Main-menu -->
                                    <div class="main-menu">
                                        <nav class="d-none d-lg-block">
                                            <ul id="navigation">
                                                <li>
                                                    <router-link to="/">
                                                        <div>Home</div>
                                                    </router-link>
                                                </li>
                                                <li>
                                                    <router-link to="/">
                                                        <div>About</div>
                                                    </router-link>
                                                </li>
                                                <li>
                                                    <router-link to="/">
                                                        <div>Contact</div>
                                                    </router-link>
                                                </li>
                                            </ul>
                                        </nav>
                                    </div>
                                    <!-- Header-btn -->
                                    <div class="header-btn d-none f-right d-lg-block">
                                        <router-link to="/">
                                            <button @click="showRegisterModal" class="btn head-btn1">Register</button>
                                        </router-link>

                                        <router-link to="/">
                                            <button @click="showLoginModal" class="btn head-btn2">Login</button>
                                        </router-link>
                                    </div>
                                </div>
                            </div>
                            <!-- Mobile Menu -->
                            <div class="col-12">
                                <div class="mobile_menu d-block d-lg-none"></div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </header>
        <Login @close="closeLoginModal"></Login>
        <Register @close="closeRegisterModal"></Register>
    </div>
</template>

<script>
import Login from "./components/Jobs/Login";
export default {
    name: "Header",
    components: {Login},
    data() {
        return {
            login: {
                email: '',
                password: '',
            },
            registration: {
                name: '',
                email: '',
                password: '',
                password_confirmation: ''
            },
            currentRoute: '',
            user: '',
            isLog: 0,
            reset: {
                email: '',
                password: '',
            },
            loginError: '',


        }
    },
    created() {

    },
    methods: {
        log() {
            axios.post('/api/login', this.login
            ).then(response => {
                console.log("********", response.data.error);
                if (response.data.error) {
                    this.loginError = response.data.error;
                } else {
                    localStorage.setItem("user", JSON.stringify(response.data.user, response.data.token));
                    localStorage.setItem("token", JSON.stringify(response.data[0].token));
                    this.$router.push({path: "/user-dashboard"});
                    console.log('***++', this.$router.currentRoute.name)
                    this.currentRoute = this.$router.currentRoute.name;
                }
                this.login.email = '';
                this.login.password = '';

            });

        },
        register() {
            axios.post('/api/register',
                this.registration
            ).then(response => {
                console.log(response.data);
            });
            location.reload();
            this.$router.push({path: "/"});

        },
        logout() {
            localStorage.removeItem("user");
            localStorage.removeItem("token");
            this.$router.push({path: "/"});
            location.reload();
        },
        resetPassword() {
            axios.post('/api/reset-password',
                this.reset
            ).then(response => {
                console.log(response.data);
            });
            location.reload();
        },
        showLoginModal() {
            $("#login-modal").modal('show');
        },
        showRegisterModal() {
            $("#register-modal").modal('show');
        },
        closeLoginModal() {
            $("#login-modal").modal('close');
        },
        closeRegisterModal() {
            $("#register-modal").modal('close');
        }
    }
}
</script>

<style scoped>

</style>
