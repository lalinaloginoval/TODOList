<template>
  <div class="app">
    <div class="input-group">
      <input
        v-model="inputValue"
        @keyup.enter="addItem"
        type="text"
        class="input-item"
      />
      <span class="input-button">
        <button class="button-add" @click="addItem">Добавить</button>
      </span>
    </div>
    <ToDoItem
      v-for="(item, index) in list"
      :key="item.id"
      :item="item"
      @remove="removeTask(index)"
    />
  </div>
</template>

<script>
import ToDoItem from "./components/ToDoItem.vue";

export default {
  components: {
    ToDoItem,
  },
  data: () => ({
    inputValue: "",
    list: [],
  }),
  methods: {
    addItem() {
      this.list.push({
        title: this.inputValue,
        done: false,
      });

      this.inputValue = "";
      console.log(this.list);
    },
    removeTask(index) {
      this.list.splice(index, 1);
    },
  },
};
</script>

<style>
.app {
  width: 100%;
  max-width: 45rem;
  padding: 1em;
  margin: 1em auto;
  overflow: auto;
  background-color: white;
  box-shadow: 0px 0.25rem 1rem rgb(0 0 0 / 25%);
  border: 1px solid #d2d1d1;
}
input {
  display: block;
  box-sizing: border-box;
  width: 100%;
  height: 2.4375rem;
  padding: 0.5rem;
  border: 1px solid #cacaca;
  margin: 0 0 1rem;
  font-family: inherit;
  font-size: 1rem;
  color: #0a0a0a;
  background-color: #fefefe;
  box-shadow: inset 0 1px 2px hsl(0deg 0% 4% / 10%);
  border-radius: 0;
}
.input-group {
  position: relative;
  display: table;
  width: 100%;
  margin-bottom: 1rem;
}
.input-button {
  padding-top: 0;
  padding-bottom: 0;
  text-align: center;
  height: 100%;
  width: 1%;
}
.button-add {
  display: inline-block;
  text-align: center;
  line-height: 1;
  cursor: pointer;
  transition: background-color 0.25s ease-out, color 0.25s ease-out;
  vertical-align: middle;
  border: 1px solid transparent;
  border-radius: 0;
  padding: 0.85em 1em;
  margin: 0 0 1rem;
  font-size: 0.9rem;
  background-color: #2199e8;
  color: #fefefe;
}
.input-button,
.input-item {
  margin: 0;
  white-space: nowrap;
  display: table-cell;
  vertical-align: middle;
}
</style>
