<template>
  <div class="row">
    <div class="columns">
      <div class="column">
        <div class="field is-grouped" v-for="(todo, idx) in todos" :key="idx">
          <p class="control">
            <a class="button is-rounded is-small check-button" @click="check(idx)">
              <span class="icon is-small"></span>
            </a>
          </p>
          <p class="control is-expanded" :class="{'checked': todo.checked }">{{todo.description}}</p>
          <p class="control">
            <a class="button is-danger is-small" @click="remove(idx)">
              <span class="icon is-small">
                <i class="fa fa-trash"></i>
              </span>
            </a>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "todo-list",
  props: ["todos"],
  data() {
    return {};
  },
  methods: {
    check(idx) {
      this.$emit("check", idx);
    },
    remove(idx) {
      this.$emit("remove", idx);
    }
  }
};
</script>

<style scoped>
.button {
  border-radius: 50%;
}
.checked {
  text-decoration: line-through;
}
</style>