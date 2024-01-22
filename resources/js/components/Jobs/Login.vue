<template>
    <div id="login-modal" class="modal fade col-md-12 mx-auto" tabindex="-1" role="dialog"
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
                    <form class="form" role="form">
                        <div class="form-group">
                            <input v-model="login.email" id="emailInput" placeholder="Email" class="form-control form-control-sm" type="email" required="">
                        </div>
                        <div class="form-group">
                            <input v-model="login.password" id="passwordInput" placeholder="Password" class="form-control form-control-sm" type="password" required="">
                        </div>
                        <div class="form-group" v-if="loginError">
                            <p style="color: red">{{loginError}}</p>
                        </div>
                        <div class="form-group">
                            <button type="button" id="loginBtn" class="btn btn-primary btn-block" @click="log()" data-toggle="dropdown">Login</button>
                        </div>
                        <div class="form-group text-center">
                            <small><a href="#" data-toggle="modal" data-target="#modalPassword">Forgot password?</a></small>
                        </div>
                    </form>
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
    name: "Login",
    data(){
      return {
          login:{
              email:'',
              password:'',
          },
          reset:{
              email:'',
              password:'',
          },
          loginError:'',
      }
    },
    methods: {
        close() {
            this.$emit("close"); // Emit `close` event to parent component
        },
        log() {
            axios.post('/api/login', this.login
            ).then(response => {
                console.log("********", response.data.error);
                if (response.data.error) {
                    this.loginError =response.data.error;
                } else {
                    localStorage.setItem("user", JSON.stringify(response.data.user, response.data.token));
                    localStorage.setItem("token", JSON.stringify(response.data[0].token));
                    this.$router.push({path: "/user-dashboard"});
                    console.log('***++',this.$router.currentRoute.name)
                    this.currentRoute = this.$router.currentRoute.name;
                    this.close();
                }
                this.login.email = '';
                this.login.password = '';

            });
        },
        logout(){
            localStorage.removeItem("user");
            localStorage.removeItem("token");
            this.$router.push({path: "/"});
            location.reload();
        }
    },
}
</script>

<style scoped>
.modal-body {
    text-align: center;
}
#login-modal {
    margin-top: 10em;
}
</style>
