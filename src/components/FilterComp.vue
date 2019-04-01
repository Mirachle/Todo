<template>
  <div>
    <h4 @click="itemClicked(item,index)" v-for="(item,index) in list" :key="index" class="filter">
      <filter-list-item :item="item" :selected="cl(index)"/>
    </h4>
  </div>
</template>

<script>
import FilterListItem from "@/components/FilterListItem";
export default {
  name: "FilterComp",
  components: {
    "filter-list-item": FilterListItem
  },
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
  data() {
    return {
      list: ["All", "Pending", "Done"],
      selectedIndex: undefined
    };
  },
  methods: {
    itemClicked(value, index) {
      this.selectedIndex = index;
      this.$emit("filterType", value);
    },
    cl(index) {
      return this.selectedIndex === index;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.filter {
  display: inline-flex;
  padding: 0 10px;
  cursor: pointer;
}
</style>
