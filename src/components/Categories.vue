<script>

    import iconApartment from '@/assets/icon-apartment.png';
    import iconLuxury from '@/assets/icon-luxury.png';
    import iconHotel from '@/assets/icon-condominium.png';
    import iconHouse from '@/assets/icon-neighborhood.png';

    export default{
        data(){
            return{
                iconApartment,
                iconLuxury,
                iconHotel,
                iconHouse
            }
        },

    }
</script>
<template>
     <div class="container-xxl py-5">
            <div class="container">
                <div class="text-center mx-auto mb-5 wow fadeInUp" data-wow-delay="0.1s" style="max-width: 600px;">
                    <h1 class="mb-3">Szállástipusok</h1>
                    <p>Válaszd ki azt a szállástípust, ami megfelelő neked</p>
                </div>
                <div class="row g-4">
                    <div class="col-lg-3 col-sm-6 wow fadeInUp" data-wow-delay="0.1s">
                        <a class="cat-item d-block bg-light text-center rounded p-3" href="">
                            <div class="rounded p-4">
                                <div class="icon mb-3">
                                    <img class="img-fluid" :src="iconApartment" alt="Apartment Icon">
                                </div>
                                <h6>Apartman</h6>
                                <span>0 Található</span>
                            </div>
                        </a>
                    </div>
                    <div class="col-lg-3 col-sm-6 wow fadeInUp" data-wow-delay="0.3s">
                        <a class="cat-item d-block bg-light text-center rounded p-3" href="">
                            <div class="rounded p-4">
                                <div class="icon mb-3">
                                    <img class="img-fluid" :src="iconLuxury" alt="Luxury Icon">
                                </div>
                                <h6>Luxus ingatlan</h6>
                                <span>123 Található</span>
                            </div>
                        </a>
                    </div>
                    <div class="col-lg-3 col-sm-6 wow fadeInUp" data-wow-delay="0.1s">
                        <a class="cat-item d-block bg-light text-center rounded p-3" href="">
                            <div class="rounded p-4">
                                <div class="icon mb-3">
                                    <img class="img-fluid" :src="iconHotel" alt="Hotel Icon">
                                </div>
                                <h6>Szálloda</h6>
                                <span>123 Található</span>
                            </div>
                        </a>
                    </div>
                    <div class="col-lg-3 col-sm-6 wow fadeInUp" data-wow-delay="0.3s">
                        <a class="cat-item d-block bg-light text-center rounded p-3" href="">
                            <div class="rounded p-4">
                                <div class="icon mb-3">
                                    <img class="img-fluid" :src="iconHouse" alt="House Icon">
                                </div>
                                <h6>Családi ház</h6>
                                <span>123 Található</span>
                            </div>
                        </a>
                    </div>
                </div>
            </div>
        </div>
</template>
<style scoped>

</style>