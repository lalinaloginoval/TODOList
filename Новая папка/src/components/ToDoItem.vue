<template>
  <div class="to_do">
    <button :class="className" @click.self="completeTask(item)">
      {{ item.title }}
    </button>
    <button
      class="task_remove button alert pull-right"
      @click="$emit('remove')"
    >
      Удалить
    </button>
  </div>
</template>

<script>
export default {
  props: {
    item: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    completeTask(item) {
      item.done = !item.done;
    },
  },
  computed: {
    className() {
      let classes = ["task_toggle"];
      if (this.item.done) {
        classes.push("task_toggle--completed");
      }
      return classes.join(" ");
    },
  },
};
</script>

<style scoped>
.task_toggle {
  cursor: pointer;
  width: 100%;
  text-align: left;
  padding: 0.85em 2.25em 0.85em 1em;
  background-color: rgba(0, 0, 0, 0.05);
  border: 1px solid rgba(0, 0, 0, 0.1);
}
.task_toggle--completed {
  text-decoration: line-through;
  background-color: rgba(0, 128, 0, 0.15);
  border-color: rgba(0, 128, 0, 0.2);
}
.task_remove {
  position: absolute;
  height: 100%;
  top: 50%;
  right: 0;
  -webkit-transform: translateY(-50%);
  transform: translateY(-50%);
}
.pull-right {
  float: right;
}
.button.alert {
  background-color: #ec5840;
  color: #fefefe;
}
.to_do {
  margin-bottom: 0.5em;
  position: relative;
}
</style>
