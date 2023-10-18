<template>
    <div>
        <img v-bind:src="image.source" v-bind:alt="image.alt" />
        <div>
            <h3>{{ name }}</h3>
            <p v-if="inStock">En stock</p>
            <p v-else>En rupture de stock</p>
            <div>
                <label for="add-item-quantity">Quantité : {{ quantity }}</label>
                <input type="number" name="add-item-quantity" id="add-item-quantity" v-model.number="geQuantity">
                <button v-on:click="addToShoppingCart(quantity)">
                    Ajouter au panier
                </button>
            </div>
        </div>
    </div>

</template>

<script>
export default {
    name: 'MenuItem',
    props: ['addToShoppingCart', 'image', 'inStock', 'name', 'quantity'],

    computed: {
        geQuantity() {
            return this.quantity
        }
    }
}
</script>

<style></style>