<template>
  <div>
    <span :class="className">
      <ic-done  :item="item"/>
      <span @click="[showModal = true, changeClassName('fadeInDown')]"><item-text>{{item.text}}</item-text></span>
      <ic-delete @clicked="request"/>
    </span>

    <modal
      v-if="showModal"
      @close="changeClassName('fadeOutDown')"
      :sendName="effectName"
      :title="item.text"
      @pressOkButton="load"
      :currentValue="item.task"
      :myDate="item.deadLine"
    ></modal>
  </div>
</template>

<script>
import IcDone from "@/components/IcDone";
import IcDelete from "@/components/IcDelete";
import ModalComp from "@/components/ModalComp";
export default {
  name: "ListItem",
  props: ["item"],
  components: {
    "ic-done": IcDone,
    "ic-delete": IcDelete,
    "modal": ModalComp
  },
  data() {
    return {
      className: "item-class",
      showModal: false,
      effectName: ""
    };
  },
  methods: {
    request() {
      this.$emit("deleteRequest", this.item);
    },
  /* isDone(value) {
      this.item.isDone = value;
    },*/
    load(areaValue, deadLine) {
      this.effectName = "fadeOutDown";
      this.item.task = areaValue;
      this.item.deadLine = deadLine;
    },
    changeClassName(value) {
      this.effectName = value;
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

item-text{
  cursor: pointer;
}

</style>
