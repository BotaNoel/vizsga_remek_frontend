<script>
export default {
    data(){
        return{
            newProfile:{
                name:"",
                email:"",
                password:""
            }
        }
    },
    methods: {
        upload() {
            this.$emit('upload')
                fetch("http://127.0.0.1:8000/api/register", {
                    method: "POST",
                    headers: {
                        "Content-Type": "application/json"
                    },
                    body: JSON.stringify({ "name": this.newProfile.name, "email": this.newProfile.email, "password": this.newProfile.password })
                })
                    .then(response => response.json())
                    .then(alert("Sikeres regisztráció"))
        }
    }
}
</script>
<template>
    <div class="container text-center mt-3 w-50">
        <div class="card">
            <h3 class="text-primary">Regisztáció</h3>
            <div class="card-body">
                <div class="mt-2">
                    <label for="name" class="form-label">név:</label>
                    <input type="text" name="name" id="name" class="form-control" v-model="newProfile.name">
                </div>
                <div class="mt-2">
                    <label for="email" class="form-label">E-mail:</label>
                    <input type="email" name="email" id="email" class="form-control" v-model="newProfile.email">
                </div>
                <div class="mt-2">
                    <label for="password" class="form-label">Jelszó:</label>
                    <input type="password" name="password" id="password" class="form-control" v-model="newProfile.password">
                </div>
                <div class="mt-2">
                    <label for="password_confirmation" class="form-label">Jelszó megerősítése:</label>
                    <input type="password" name="password_confirmation" id="rePassword" class="form-control">
                </div>
                <input type="button" value="Regisztráció" class="btn btn-primary mt-2" @click="upload()">
            </div>
        </div>
    </div>
</template>
<style></style>