<template>
  <li class="list-group-item shop-item" v-bind:class="{ completed: completed }">
    <input
      class="form-check-input checkbox-item"
      type="checkbox"
      value=""
      id="flexCheckDefault"
      v-model="completed"
    />
    {{ item.name }}
  </li>
</template>

<script>
export default {
  name: "ShoppingItem",
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      completed: this.item.completed,
    };
  },
};
</script>

<style scoped>
.shop-item {
  text-align: left;
}

.checkbox-item {
  margin-right: 10px;
}

.completed {
  text-decoration: line-through;
  color: gray;
}
</style>
