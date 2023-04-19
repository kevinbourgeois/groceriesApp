<template>
  <form>
    <label> Article :
      <input type="text" placeholder="Frozen pizza" v-model="article">
    </label>

    <label> Quantité :
      <input type="number" v-model="quantity">
    </label>

    <label>
      <select v-model="category">
        <option disabled>Choissisez une catégorie</option>
        <option>🍎</option>
        <option>🍺</option>
        <option>🧀</option>
        <option>🍫</option>
        <option>🥘</option>
        <option>🏡</option>
      </select>
    </label>

    <button @click="addArticle">Soumettre</button>
  </form>

  <label> Filtrer par :
    <select @change="filterGroceries" v-model="filterCategory">
      <option disabled>Choissisez une catégorie</option>
      <option>all</option>
      <option>🍎</option>
      <option>🍺</option>
      <option>🧀</option>
      <option>🍫</option>
      <option>🥘</option>
      <option>🏡</option>
    </select>

  </label>

  <li v-for="item in list" v-bind:key="item.id">


    {{ item.quantity }}x {{ item.name }} {{item.category}}
    <button @click="removeArticle">In the cart !</button>
  </li>




</template>

<script>
import {ref} from "vue";

export default {
  data() {
    return {
      article: '',
      quantity: 0,
      category: '',
      filterCategory: '',
      list: this.groceries
    }
  },
  name: "FormGroceries",
  setup() {
    const groceries = ref([]);

    return {
      groceries
    }
  },
  methods: {
    addArticle: function (event) {
      event.preventDefault()

      const article = {
        name: this.article,
        quantity: this.quantity,
        category: this.category
      }

      this.groceries.push(article)
    },
    removeArticle: function (id) {
      this.groceries.splice(id, 1);
    },
    filterGroceries: function () {
      const filterArray = []

      if (this.category === 'all'){
        this.list = this.groceries
      } else {
        this.groceries.forEach(item => {
          if (item.category === this.filterCategory) {
            filterArray.push(item)
          }
        })

        this.list = filterArray
      }







    }
  }
}
</script>

<style scoped>
form {
  display: flex;
  justify-content: space-evenly;
}
</style>