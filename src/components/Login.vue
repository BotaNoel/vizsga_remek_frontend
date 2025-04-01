<script>
import bg from '@/assets/login_bg.png'
import Register from '@/components/Register.vue'
import Reset from '@/components/Reset.vue'

export default {
    components: {
        Register,
        Reset
    },
    data() {
        return {
            bg,
            register: false,
            reset: false,
            users: [],
            user: {
                email: "",
                password: ""
            },
            loginError: '',  // A hibaüzenetek itt lesznek tárolva
            authToken: '',  // A token itt lesz tárolva
            loggedInUser: {} // A bejelentkezett felhasználó információi
        }
    },
    methods: {
        registerSite() {
            this.register = !this.register
        },
        login() {
            console.log(this.user)
            fetch("http://127.0.0.1:8000/api/login", {
                method: "POST",
                headers: {
                    "Accept": "application/json",
                    "Content-Type": "application/json"
                },
                body: JSON.stringify({ "email": this.user.email, "password": this.user.password })
            })
                .then(response => response.json())
                .then(data => {
                    if (data.token) {
                        // Ha van token, sikeres a bejelentkezés
                        this.authToken = data.token;
                        this.loggedInUser = data.user;
                        localStorage.setItem("authToken", data.token);
                        localStorage.setItem("loggedInUser", JSON.stringify(data.user));
                        this.$emit('logged_in', data.user);
                        this.$router.push('/'); // Átirányítás a főoldalra
                    } else {
                        // Ha nincs token, hiba történt
                        this.loginError = data.message || 'Hiba történt a bejelentkezés során'; // A hibaüzenet megjelenítése
                    }
                })
                .catch(error => {
                    console.error("Login failed:", error);
                    this.loginError = 'Hiba történt a kapcsolat során';
                });
        }
    },
    mounted() {
    const token = localStorage.getItem("authToken");
    const user = localStorage.getItem("loggedInUser");

    if (token && user) {
        this.authToken = token;
        this.loggedInUser = JSON.parse(user);
        this.$emit('logged_in', this.loggedInUser);
    }
}
}
</script>

<template>
    <div v-if="!register && !reset">
        <div class="container mt-3 text-center w-50">
            <div class="card">
                <h3 class="card-title text-primary">Bejelentkezés</h3>
                <div class="card-body">
                    <div class="mt-2">
                        <label for="email" class="form-label text-start">E-mail cím:</label>
                        <input type="email" id="email" v-model="user.email" class="form-control">
                    </div>
                    <div class="mt-2">
                        <label for="password" class="form-label">Jelszó:</label>
                        <input type="password" name="password" id="password" v-model="user.password"
                            class="form-control">
                    </div>
                    <div v-if="loginError" class="mt-3 text-danger">
                        <p>{{ loginError }}</p>
                    </div>
                    <input type="button" value="Bejelentkezés" @click="login" class="mt-2 btn btn-primary">
                    <div class="mt-5 row">
                        <div class="col-lg-6 col-12">
                            <p>Nincs még fiókod? regisztrálj:</p>
                            <input type="button" @click="registerSite()" value="Regisztráció"
                                class="mt-2 btn btn-primary">
                        </div>
                        <div class="col-lg-6 col-12">
                            <p>Elfelejetted a jelszót?</p>
                            <input type="button" value="Jelszó visszaállítása" @click="resetSite()"
                                class="mt-2 btn btn-primary">
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <div v-else-if="reset && !register">
        <Reset @upload="resetSite" />
    </div>
    <div v-else-if="register && !reset">
        <Register @upload="registerSite" />
    </div>
</template>

<style>
.card {
    background-color: transparent;
    border: transparent;
}
</style>
