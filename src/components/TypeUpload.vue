<script>
    
    export default{
    components:{
      ApartmentUpload
    },
    data(){
        return{
            types:[],
            type_id:0,
            apartmentSite:false
        }
    },
    mounted(){
      this.fetchTypes();
      this.apartmentSite = false
    },
    methods:{
      nextSite(){
        this.apartmentSite = true
      },
      async fetchTypes() {
            try {
                const response = await fetch('http://localhost:8000/api/types', {
                    method: 'GET',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                });
                if (response.ok) {
                    const data = await response.json();
                    this.types = data;
                    console.log(this.types)
                } else {
                    console.error('Hiba történt a felhasználók lekérésekor');
                }
            } catch (error) {
                console.error('Hálózati hiba történt', error);
            }
        },
    }
  }
</script>
<template>
  <div v-if="!apartmentSite">
    <div class="container">
    <div class="card text-center">
      <div>
        <h3 class="card-title text-primary">Tipusválasztás</h3>
        <div class="card-body text-primary">
          <div class="mt-2">
            <label for="type" class="form-label">Szállástipus</label>
            <select name="type" id="type" class="form-control" v-model="type_id">
              <option v-for="type in types" :value="type.id">{{type.type_name}}</option>
            </select>
          </div>
          <input type="button" value="Tovább" class="btn btn-primary mt-2" @click="nextSite()">
        </div>
      </div>
    </div>
  </div>
  </div>
  <div v-else-if="apartmentSite">
    <ApartmentUpload :type_id="type_id"/>
  </div>
</template>
<style>

</style>