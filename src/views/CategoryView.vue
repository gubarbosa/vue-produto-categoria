<script>
import { mapState, mapStores, mapActions } from "pinia";
import { useCategoryStore } from "@/stores/category";
export default {
  data() {
    return {
      currentCategory {
        id "",
        description "",
      }
    }
  }
  computed: {
    ...mapStores(useCategoryStore),
    ...mapState(useCategoryStore, ["categories"]),
  },
  methods: {
    ...mapActions(useCategoryStore, ["getAllCategories", ""]),
    save() {
      this.saveCategory(this.currentCategory);
    },
  },
  mounted() {
    this.getAllCategories();

  },
};
</script>

<template>
  <h1>Cadastro de Categorias</h1>
  <div class="category-form"></div>
  <input type="text" v-model="currentCategory.description"/>
  <button>Adicionar</button>
  <div class="category-list">
    <table class="table">
      <tr>
        <th class="text-left">
          <span>
            <h2>ID</h2>
          </span>
        </th>
        <th class="text-left">
          <span>
            <h2>Descrição</h2>
          </span>
        </th>
        <th class="text-left">
          <span>
            <h2>Ações</h2>
          </span>
        </th>
      </tr>
    </table>
  </div>
  <body>
    <tr v-for"category of categories" key: "category.id">
      <th>{{category.id}} </th>
      <th>{{category.description</th>
  </body>
</template>

.category-form input {
  width: 75px;
  height: 40px;
  border-radius: 20px;
  border: 1px solid gray;
  padding-left: 20px;
  font-size: 1.2em;
}

.category-form button {
  height: 35px;
  width: 20px;
  margin-left: 2px;
  background-color: rgb(63,63, 125);
  color: 20px;
  border: 0;
}
<style>
.category-list {
  margin: 0 auto;
  width: 70px;
  display: flex;
  justify-content: center;

}
table {
  border-collapse: separate;
  border-spacing: 2px;
  border-color: gray;
  width: 100%;
}

th {
  border-bottom: 2px solid black;
  text-align: left;
}
</style>
