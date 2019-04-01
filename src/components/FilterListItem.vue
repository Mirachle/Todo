<template>
  <div>
    <span :class="className">{{item}}</span>
  </div>
</template>

<script>
export default {
  name: "FilterListItem",
  props: {
    selected: {
      type: Boolean,
      required: true
    },
    item: {
      type: String,
      required: true
    }
  },
  computed: {
    className() {
      if (this.selected) {
        return "select";
      }
      return "";
    }
  }
};
</script>

<style scoped>
.select {
  color: green;
}
span {
  font-weight: bold;
}
</style>
