<template>
  <span :class="className">
    <ic-done @isDone="isDone" :item="item"/>
    {{item}}
    <ic-delete @clicked="request"/>
  </span>
</template>

<script>
import IcDone from "@/components/IcDone";
import IcDelete from "@/components/IcDelete";
export default {
  name: "ListItem",
  props: ["item"],
  components: {
    "ic-done": IcDone,
    "ic-delete": IcDelete
  },
  data() {
    return {
      className: "item-class"
    };
  },
  methods: {
    request() {
      this.$emit("deleteRequest", this.index);
      //alert(this.index)
    },
    isDone(value){
      this.item.isDone = value
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.item-class {
  background-color: white;
  display: block;
  margin: 2% 5% 2% 5%;
  text-align: left;
  padding: 8px 8px 8px 8px;
  border-radius: 5px;
  position: relative;
  box-shadow: 0px 0px 10px 5px #bebebe;
}
span {
  font-weight: bold;
}
</style>
