<template>
  <div id="app">
    <div class="top-container">
      <div class="selected-items-left">
        <h3>Selected Items (Left):</h3>
        <div v-for="item in selectedItemsLeft" :key="item.id" class="item">
          {{ item.name }}
        </div>
      </div>
      <div class="selected-item-right">
        <h3>Selected Item (Right):</h3>
        <div v-if="selectedItemRight" class="item">
          {{ selectedItemRight.name }}
        </div>
      </div>
    </div>
    <div class="bottom-container">
      <div class="items-left">
        <h3>Items (Left):</h3>
        <div
          v-for="item in itemsLeft"
          :key="item.id"
          class="item"
          @click="selectItemLeft(item)"
        >
          {{ item.name }}
        </div>
      </div>
      <div class="items-right">
        <h3>Items (Right):</h3>
        <div
          v-for="item in itemsRight"
          :key="item.id"
          class="item"
          @click="selectItemRight(item)"
        >
          {{ item.name }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      itemsLeft: [
        { id: 1, name: "Shoes 1" },
        { id: 2, name: "Shoes 2" },
        { id: 3, name: "Shoes 3" },
        { id: 4, name: "Shoes 4" },
        { id: 5, name: "T-shirt 1" },
        { id: 6, name: "T-shirt 2" },
        { id: 7, name: "T-shirt 3" },
        { id: 8, name: "T-shirt 4" },
      ],
      itemsRight: [
        { id: 11, name: "Jacket 1" },
        { id: 12, name: "Jacket 2" },
        { id: 13, name: "Jacket 3" },
        { id: 14, name: "Jacket 4" },
        { id: 15, name: "Hoodie 1" },
        { id: 16, name: "Hoodie 2" },
        { id: 17, name: "Hoodie 3" },
        { id: 18, name: "Hoodie 4" },
      ],
      selectedItemsLeft: [],
      selectedItemRight: null,
    };
  },
  methods: {
    selectItemLeft(item) {
      if (this.selectedItemsLeft.length < 6) {
        this.selectedItemsLeft.push(item);
      }
    },
    selectItemRight(item) {
      this.selectedItemRight = item;
    },
  },
};
</script>

<style lang="scss">
$primary-color: #3498db;
$secondary-color: #2ecc71;
$background-color: #ecf0f1;
$border-color: #bdc3c7;
$hover-color: darken($background-color, 10%);
$font-family: "Avenir", Helvetica, Arial, sans-serif;

#app {
  font-family: $font-family;
  text-align: center;
  background-color: $background-color;
  padding: 20px;

  .top-container,
  .bottom-container {
    display: flex;
    justify-content: space-around;
    margin-bottom: 20px;
  }

  .selected-items-left,
  .selected-item-right,
  .items-left,
  .items-right {
    border: 1px solid $border-color;
    padding: 20px;
    width: 45%;
    background-color: white;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    transition: transform 0.2s;

    &:hover {
      transform: scale(1.05);
    }
  }

  .item {
    border: 1px solid $border-color;
    margin: 10px;
    padding: 15px;
    cursor: pointer;
    background-color: $primary-color;
    color: white;
    text-align: center;
    border-radius: 5px;
    transition: background-color 0.2s, box-shadow 0.2s;

    &:hover {
      background-color: $secondary-color;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    }
  }
}
</style>
