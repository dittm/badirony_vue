<template>
    <div class="page-search">
        <div class="columns is-multiline">
            <div class="column is-12">
                <h2 class="is-size-2 has-text-centered">Search</h2>

                <h2 class="is-size-5">Search term: "{{ query }}"</h2>
            </div>

            <ProductBox 
                v-for="product in products"
                v-bind:key="product.id"
                v-bind:product="product" />
        </div>
    </div>
</template>

<script>
import axios from 'axios'
import ProductBox from '@/components/ProductBox.vue'

export default {
    name: 'Search',
    components: {
        ProductBox
    },
    data() { 
        return {
            products: [],
            query: ''   // returns the data object for the component
        }
    },
    mounted() { // vue lifecycle hook: runs after the Vue component is mounted on the DOM
        document.title = 'Search | Bad Irony'

        let uri = window.location.search.substring(1) // gets search parameters from the url
        let params = new URLSearchParams(uri)

        if (params.get('query')) {
            this.query = params.get('query')

            this.performSearch()
        }
    },
    methods: {
        async performSearch() {
            this.$store.commit('setIsLoading', true)  

            await axios
                .post('/api/v1/products/search/', {'query': this.query})
                .then(response => {
                    this.products = response.data
                })
                .catch(error => {
                    console.log(error)
                })

            this.$store.commit('setIsLoading', false)
        }
    }
}   // this inside the arrow function has the same value as this in the performSearch method, which allows you to directly modify the products data property.
</script>