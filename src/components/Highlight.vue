<script>

    import highlighted from '@/assets/highlighted.jpg';

    export default{
    data(){
        return{
            highlighted
        }
    }
  }

</script>
<template>
        <div class="container-xxl py-5">
            <div class="container">
                <div class="row g-5 align-items-center">
                    <div class="col-lg-6 wow fadeIn" data-wow-delay="0.1s">
                        <div class="about-img position-relative overflow-hidden p-5 pe-0">
                            <img class="img-fluid w-100" :src="highlighted" alt="Image">
                        </div>
                    </div>
                    <div class="col-lg-6 wow fadeIn" data-wow-delay="0.5s">
                        <h1 class="mb-4">Kiemelt ajánlatunk</h1>
                        <p class="mb-4">Budapest szívében található</p>
                        <p><i class="fa fa-check text-primary me-3"></i>Luxus</p>
                        <p><i class="fa fa-check text-primary me-3"></i>All-inclusive</p>
                        <p><i class="fa fa-check text-primary me-3"></i>Közel a központhoz</p>
                        <a class="btn btn-primary py-3 px-5 mt-3" href="">Read More</a>
                    </div>
                </div>
            </div>
        </div>
</template>
<style scoped>

</style>