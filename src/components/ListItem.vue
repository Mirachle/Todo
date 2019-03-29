<template>
<div>
  <span :class="className">
    <ic-done @isDone="isDone" :item="item"/>
<<<<<<< HEAD
    <span @click="showModal = true">{{item.text}}</span>
=======
    {{item.text}}
>>>>>>> 1d2bb1583e5252773d333cb5d2c2c8c5b5e137a2
    <ic-delete @clicked="request"/>
  </span>

  <modal v-if="showModal" @close="showModal = false">
    <h3 slot="header">custom header</h3>
  </modal>
</div>
</template>

<script>
import IcDone from "@/components/IcDone";
import IcDelete from "@/components/IcDelete";
import ModalComp from "@/components/ModalComp"
export default {
  name: "ListItem",
  props: ["item"],
  components: {
    "ic-done": IcDone,
    "ic-delete": IcDelete,
    "modal": ModalComp,
  },
  data() {
    return {
      className: "item-class",
      "showModal" : false
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
