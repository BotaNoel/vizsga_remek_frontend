<script>
export default {
    methods: {
        upload() {
            this.$emit('upload')
            fetch("http://localhost/api/foglalasok", {
                method: "POST",
                headers: {
                    "Content-Type": "application/json"
                },
                body: JSON.stringify({ "nev": this.ujfoglalas.nev, "darab": this.ujfoglalas.fo, "jaratszam": this.jaratszam })
            })
                .then(response => response.json())
                .then(alert("Sikeres foglalás"))
        }
    }
}
</script>
<template>
    <div class="container w-50 text-center">
        <div class="card">
            <h3 class="card-title text-primary">Jelszó visszaállítása</h3>
            <div class="card-body">
                <div class="mt-2">
                    <label for="email" class="form-label">E-mail:</label>
                    <input type="email" class="form-control" name="email" id="email">
                </div>
                <input type="button" value="Jelszó visszaállítáas" @click="upload" class="mt-2 btn btn-primary">
            </div>
        </div>
    </div>
</template>
<style></style>