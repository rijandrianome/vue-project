<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <div id="app">
      <nav>
          <NavLink url="/" text="Accueil"></NavLink>
          <NavLink url="/about" text="À propos"></NavLink>
          <NavLink url="/contact" text="Contact"></NavLink>
      </nav>
      <p>Bienvenue sur notre page</p>
      <div id="resto">
    <h1>{{ restaurantName }}</h1>
    <p>
        Bienvenue dans notre café {{ restaurantName }}! Nous sommes réputés pour
        notre pain et nos merveilleuses pâtisseries. Faites vous plaisir dès le
        matin ou avec un goûter réconfortant. Mais attention, vous verrez qu'il
        est difficile de s'arrêter.
    </p>

    <section>
        <h2>Menu</h2>
        <MenuItem
            v-for="item in simpleMenu"
            :addToShoppingCart="addToShoppingCart"
            :key="item.name"
            :name="item.name"
            :quantity="item.quantity"
            :inStock="item.inStock"
            :image="item.image">
        </MenuItem>
    </section>

    <aside>
        <h2>Panier d'achat: {{ shoppingCart }} articles</h2>
    </aside>
</div>
  </div>
</template>

<script>
import NavLink from './components/NavLink.vue';
import MenuItem from './components/MenuItem.vue';

export default {
  name: 'App',
  components: {
    NavLink,
    MenuItem
  },

  data() {
		return {
			address: "18 avenue du Beurre, Paris, France",
			email: "hello@cafewithavue.bakery",
			phone: "01 88 88 88 88",
			restaurantName: "La belle vue",
			shoppingCart: 0,
			simpleMenu: [
				{
					name: "Croissant",
					image: {
						source: "/images/croissant.jpg",
						alt: "Un croissant"
					},
					inStock: true,
					quantity: 1
				},
				{
					name: "Baguette de pain",
					image: {
						source: "/images/french-baguette.jpeg",
						alt: "Quatre baguettes de pain"
					},
					inStock: true,
					quantity: 1
				},
				{
					name: "Éclair",
					image: {
						source: "/images/eclair.jpg",
						alt: "Éclair au chocolat"
					},
					inStock: false,
					quantity: 1
				}
			]
		}
	},
	computed: {
		copyright() {
			const currentYear = new Date().getFullYear()

			return `Copyright ${this.restaurantName} ${currentYear}`
		}
	},
	methods: {
		addToShoppingCart(amount) {
			this.shoppingCart += amount
		}
	}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
