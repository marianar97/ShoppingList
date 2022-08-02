<template>
  <div class="container">
    <h2>Shopping List</h2>
    <div>
      <input
        type="text"
        placeholder="Enter shopping item"
        class="form-control"
        v-on:keydown.enter="getItem"
        v-model="currentItem"
      />
      <ul class="list-group mt-1">
        <shopping-item
          v-for="item in list"
          v-bind:key="item.idItem"
          :item="item"
        ></shopping-item>
      </ul>
    </div>
  </div>
</template>

<script>
import ShoppingItem from "./ShoppingItem.vue";

export default {
  name: "ShoppingList",
  components: {
    ShoppingItem,
  },
  data() {
    return {
      idItem: 2,
      currentItem: "",
      list: [],
    };
  },
  methods: {
    getItem() {
      if (this.currentItem.trim().length == 0) {
        return;
      }
      this.list.push({
        id: this.idItem,
        name: this.currentItem,
        completed: false,
      });
      this.currentItem = "";
      this.idItem++;
    },
  },
};
</script>
