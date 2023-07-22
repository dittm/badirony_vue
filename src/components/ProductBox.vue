<template>
    <div class="column is-3">
        <div class="box" style="background-color: #0a0a0a;">
            <figure class="image mb-4">
                <img v-bind:src="product.get_thumbnail">
            </figure>

            <h3 class="is-size-4" style="color: #fff;">{{ product.name }}</h3>
            <p class="is-size-6 has-text-grey" style="color: #fff;">${{ product.price }}</p>

            <router-link v-bind:to="product.get_absolute_url" class="button is-dark mt-4">View details</router-link>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ProductBox',
    props: {
        product: Object
    }
}
</script>

<style scoped>
  .image {
    margin-top: -1.25rem;
    margin-left: -1.25rem;
    margin-right: -1.25rem;
  }

.column {
  flex-basis: calc(33.33% - 1rem);
  margin-bottom: 2rem;
}
</style>