<template>
    <div>
        <div class="container-fluid mt-3">
            <div class="row">
                <div class="col mb-4">
                    <!-- component Slider -->
                    <Slider data-aos="fade-up" data-aos-once="true" />
                </div>
            </div>
        </div>
        <!-- search -->
        <div class="container-fluid search-mini">
            <div class="row">
                <div class="col input-group mx-auto">
                    <input
                        type="text"
                        v-model="keywords"
                        class="form-control search-form shadow"
                        style="width: 10%; border: 1px solid #ffffff"
                        name="q"
                        placeholder="mau belanja apa hari ini ?"
                        @keypress.enter="search"
                    />
                    <div class="input-group-append shadow">
                        <button
                            class="btn search-button"
                            @click="search"
                            type="submit"
                        >
                            <i class="fa fa-search"></i>
                        </button>
                    </div>
                </div>
            </div>
        </div>
        <div>
            <div class="col mb-5 mt-4">
                <div class="card border-0 shadow rounded-lg">
                    <div class="card-body">
                        <h5 class="font-weight-bold">
                            <i class="fa fa-shopping-bag"></i> KATEGORI
                        </h5>
                        <hr />

                        <swiper-container
                            :slidesPerView="2.5"
                            :spaceBetween="30"
                            :freeMode="true"
                            :breakpoints="{
                                768: {
                                    slidesPerView: 5.5,
                                },
                            }"
                        >
                            <swiper-slide
                                v-for="category in categories.slice(0, 8)"
                                v-bind:key="category.id"
                                data-aos="fade-up"
                                data-aos-once="true"
                            >
                                <router-link
                                    v-bind:to="{
                                        name: 'detail_category',
                                        params: { slug: category.slug },
                                    }"
                                >
                                    <div
                                        class="h-100 list-group-item font-weight-bold text-decoration-none rounded-lg"
                                    >
                                        <div class="text-center">
                                            <img
                                                v-bind:src="category.image"
                                                loading="lazy"
                                                style="width: 100px"
                                            />
                                            <hr />
                                            <label
                                                class="font-weight-bold"
                                                style="color: #3f7b70"
                                                >{{ category.name }}</label
                                            >
                                        </div>
                                    </div>
                                </router-link>
                            </swiper-slide>
                        </swiper-container>

                        <div class="mt-2 d-flex justify-content-center">
                            <router-link
                                v-bind:to="{ name: 'categories' }"
                                class="list-group-item text-center active shadow-sm font-weight-bold text-decoration-none rounded-pill"
                            >
                                LIHAT LAINNYA
                                <i class="fa fa-long-arrow-alt-right"></i>
                            </router-link>
                        </div>
                    </div>
                </div>
            </div>

            <!-- data product -->
            <div class="col mb-5">
                <div v-if="products.length > 0" class="row">
                    <div
                        v-for="product in products"
                        v-bind:key="product.id"
                        class="col-md-3 col-6 mb-3"
                    >
                        <div
                            class="card h-100 border-0 shadow rounded-lg"
                            data-aos="fade-up"
                            data-aos-once="true"
                        >
                            <span
                                v-if="product.discount > 0"
                                class="ribbon"
                            ></span>
                            <div class="card-img">
                                <img
                                    v-bind:src="product.image"
                                    loading="lazy"
                                    class="w-100"
                                    style="
                                        height: 15em;
                                        object-fit: cover;
                                        border-top-left-radius: 0.3rem;
                                        border-top-right-radius: 0.3rem;
                                    "
                                />
                            </div>
                            <div class="card-body" style="padding: 1rem">
                                <router-link
                                    v-bind:to="{
                                        name: 'detail_product',
                                        params: { slug: product.slug },
                                    }"
                                    class="card-title font-weight-bold text-dark"
                                    style="font-size: 1rem"
                                >
                                    <span
                                        v-if="product.title.length < 29"
                                        class="title-card"
                                    >
                                        {{ product.title }}
                                    </span>
                                    <span v-else class="title-card">
                                        {{
                                            product.title.substring(0, 29) +
                                            '...'
                                        }}
                                    </span>
                                </router-link>

                                <div
                                    v-if="product.discount > 0"
                                    class="discount"
                                >
                                    <small>
                                        <div class="row">
                                            <div class="col-8">
                                                <s>
                                                    Rp.
                                                    {{
                                                        moneyFormat(
                                                            product.price
                                                        )
                                                    }}
                                                </s>
                                            </div>
                                            <div
                                                class="col-4 d-flex justify-content-end"
                                            >
                                                <span
                                                    class="badge badge-pill badge-discount text-white d-flex align-items-center"
                                                >
                                                    {{ product.discount }}%
                                                    OFF</span
                                                >
                                            </div>
                                        </div>
                                    </small>
                                </div>

                                <div v-else>
                                    <small class="d-flex align-items-center">
                                        Special price for you
                                    </small>
                                </div>

                                <div
                                    class="price font-weight-bold mt-3"
                                    style="color: #105652; font-size: 1.1rem"
                                >
                                    Rp.
                                    {{
                                        moneyFormat(calculateDiscount(product))
                                    }}
                                </div>
                                <router-link
                                    v-bind:to="{
                                        name: 'detail_product',
                                        params: { slug: product.slug },
                                    }"
                                    class="btn btn-detail btn-md mt-3 btn-block shadow-md text-white font-weight-bold rounded-pill"
                                >
                                    DETAIL
                                </router-link>
                            </div>
                        </div>
                    </div>
                </div>

                <div v-else>
                    <div class="row">
                        <div
                            class="col-md-3 col-6 mb-3"
                            v-for="loader in ContentLoader"
                            v-bind:key="loader"
                        >
                            <div
                                class="card h-100 border-0 shadow rounded-lg"
                                data-aos="fade-up"
                                data-aos-once="true"
                            >
                                <div class="card-body" style="padding: 1rem">
                                    <ContentLoader
                                        viewBox="0 0 150 200"
                                        :speed="2"
                                        primaryColor="#fafafa"
                                        secondaryColor="#e2e8f0"
                                    >
                                        <rect
                                            x="21"
                                            y="178"
                                            rx="10"
                                            ry="10"
                                            width="111"
                                            height="19"
                                        />
                                        <rect
                                            x="7"
                                            y="149"
                                            rx="4"
                                            ry="4"
                                            width="138"
                                            height="9"
                                        />
                                        <rect
                                            x="6"
                                            y="3"
                                            rx="8"
                                            ry="8"
                                            width="139"
                                            height="136"
                                        />
                                        <rect
                                            x="7"
                                            y="162"
                                            rx="4"
                                            ry="4"
                                            width="71"
                                            height="8"
                                        />
                                    </ContentLoader>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Slider from '@/components/Slider';
import { computed, onMounted, ref } from 'vue';
import { useStore } from 'vuex';
import { useRouter } from 'vue-router';
import { register } from 'swiper/element/bundle';

register();

import { ContentLoader } from 'vue-content-loader';

export default {
    name: 'HomeComponent',

    components: {
        Slider,
        ContentLoader,
    },

    setup() {
        const store = useStore();
        const router = useRouter;

        onMounted(() => {
            store.dispatch('product/getProducts');
            store.dispatch('category/getCategories');
        });

        const products = computed(() => {
            return store.state.product.products;
        });

        const categories = computed(() => {
            return store.state.category.categories;
        });

        // feature search
        let keywords = ref('');
        function search() {
            store.dispatch('product/getSearchProduct', keywords.value);
            router.push('/search');
        }

        return {
            store,
            products,
            categories,
            keywords,
            search,
            ContentLoader: 4,
        };
    },
};
</script>
