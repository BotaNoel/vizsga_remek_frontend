<script>
import Categories from '@/components/Categories.vue';
import Highlight from '@/components/Highlight.vue';
import Comments from '@/components/Comments.vue';

export default {
    components: {
        Categories,
        Highlight,
        Comments
    },
    data() {
        return {
            filters: false
        }
    },
    methods: {
        filterSite() {
            this.filters = !this.filters
        }
    }
}
</script>
<template>
    <div class="container-fluid bg-primary wow fadeIn" data-wow-delay="0.1s" style="padding: 35px;">
        <div class="container">
            <div class="row g-2">
                <div class="col-md-10">
                    <div class="row g-2">
                        <div class="col-md-4">
                            <input type="text" class="form-control border-0 py-3" placeholder="Város">
                        </div>
                        <div class="col-md-4">
                            <select class="form-select border-0 py-3">
                                <option value="1">Apartman</option>
                                <option value="2">Luxus ingatlan</option>
                                <option value="3" selected>Szálloda</option>
                                <option value="4">Családi ház</option>
                            </select>
                        </div>
                        <div class="col-md-4">
                            <input type="button" value="Filterek" @click="filterSite" class="btn btn-dark w-100 h-100">
                        </div>
                    </div>
                </div>
                <div class="col-md-2">
                    <button class="btn btn-dark border-0 w-100 py-3">Keresés</button>
                </div>
            </div>
        </div>
    </div>
    <div class="container-fluid d-flex justify-content-end mt-3" v-if="filters">
    <div class="bg-dark text-light w-100 shadow-lg border-0 animated-panel">
        <div class="bg-primary text-white text-center py-2">
            <h5 class="mb-0">Szűrők</h5>
        </div>
        <div class="p-3">
            <ul class="list-group list-group-flush">
                <li class="list-group-item bg-transparent text-light d-flex justify-content-between align-items-center">
                    <div class="form-check form-switch">
                        <input class="form-check-input" type="checkbox" id="wifi">
                        <label class="form-check-label" for="wifi">WiFi</label>
                    </div>
                </li>
                <li class="list-group-item bg-transparent text-light d-flex justify-content-between align-items-center">
                    <div class="form-check form-switch">
                        <input class="form-check-input" type="checkbox" id="parking">
                        <label class="form-check-label" for="parking">Ingyenes parkolás</label>
                    </div>
                </li>
                <li class="list-group-item bg-transparent text-light d-flex justify-content-between align-items-center">
                    <div class="form-check form-switch">
                        <input class="form-check-input" type="checkbox" id="pool">
                        <label class="form-check-label" for="pool">Medence</label>
                    </div>
                </li>
                <li class="list-group-item bg-transparent text-light d-flex justify-content-between align-items-center">
                    <div class="form-check form-switch">
                        <input class="form-check-input" type="checkbox" id="gym">
                        <label class="form-check-label" for="gym">Edzőterem</label>
                    </div>
                </li>
                <li class="list-group-item bg-transparent text-light d-flex justify-content-between align-items-center">
                    <div class="form-check form-switch">
                        <input class="form-check-input" type="checkbox" id="petFriendly">
                        <label class="form-check-label" for="petFriendly">Állatbarát</label>
                    </div>
                </li>
            </ul>
        </div>
        <div class="text-center p-3">
            <button class="btn btn-success w-100">Alkalmazás</button>
        </div>
    </div>
</div>
    <Categories />

    <Highlight />

    <Comments />
</template>
<style>
        @keyframes fadeIn {
        from {
            opacity: 0;
            transform: translateY(20px);
        }
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    /* Animáció alkalmazása */
    .animated-panel {
        animation: fadeIn 0.4s ease-in-out;
    }
</style>