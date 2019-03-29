<template>
  <div>
    <div v-for="(item,index) in filteredList" :key="index">
      <list-item :item="item" :index="index" @deleteRequest="request"/>
    </div>
  </div>
</template>

<script>
import ListItem from "@/components/ListItem";

export default {
  name: "ListComp",
  props: ["list", "filterName"],
  components: {
    "list-item": ListItem,
  },

  methods: {
    request(value) {
      this.$emit("deleteItemName", value)
      alert(this.filterName)
    },
    currentFilter(item){
      if(this.filterName == "Done"){
        return item.isDone
        }
      else if(this.filterName == "Pending"){
        return !item.isDone
      }
      return true
    }
  },

  computed: {
  filteredList(){
    return this.list.filter(this.currentFilter)
  }
}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
