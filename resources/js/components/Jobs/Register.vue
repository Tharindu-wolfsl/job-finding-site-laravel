<template>
    <div id="register-modal" class="modal fade col-md-12 mx-auto" tabindex="-1" role="dialog"
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
                            <input v-model="registration.name" id="RegiNameInput" placeholder="Name" class="form-control form-control-sm" type="text" required="">
                        </div>
                        <div class="form-group">
                            <input v-model="registration.email" id="RegiEmailInput" placeholder="Email" class="form-control form-control-sm" type="email" required="">
                        </div>
                        <div class="form-group">
                            <input v-model="registration.password" id="RegiPassowrdInput" placeholder="Password" class="form-control form-control-sm" type="password" required="">
                        </div>
                        <div class="form-group">
                            <input v-model="registration.password_confirmation" id="RegiConfirmPasswordInput" placeholder="Confirm Password" class="form-control form-control-sm" type="password" required="">
                            <p class="text-warning small">* Must similar with above password</p>
                        </div>
                        <div class="form-group">
                            <button type="button" class="btn btn-primary btn-block" @click="register()" data-toggle="dropdown">Register</button>
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
    name: "Register",
    data(){
        return{
            registration:{
                name:'',
                email:'',
                password:'',
                password_confirmation:''
            },
            currentRoute:'',
            user:'',
            isLog:0,
            loginError:'',
        }
    },
    methods: {
        close() {
            this.$emit("close"); // Emit `close` event to parent component
        },
        register(){
            axios.post('/api/register',
                this.registration
            ).then(response => {
                console.log(response.data);
            });
            location.reload();
            this.$router.push({path: "/"});
        },
    },
}
</script>

<style scoped>
.modal-body {
    text-align: center;
}
#register-modal {
    margin-top: 10em;
}
</style>
