<template>
<div>
  <span :class="className">
    <ic-done @isDone="isDone" :item="item"/>
    <span @click="showModal = true">{{item.text}}</span>
    <ic-delete @clicked="request"/>
  </span>

  <modal v-if="showModal" @close="showModal = false" :hea="item.text" @pressOkButton="load" :currentValue="taskContent" :myDate="taskDeadLine">
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
      "showModal" : false,
      "taskContent": "",
      "taskDeadLine": ""
    };
  },
  methods: {
    request() {
      this.$emit("deleteRequest", this.index);
      //alert(this.index)
    },
    isDone(value){
      this.item.isDone = value
    },
    load(areaValue,deadLine){
      this.showModal=false,
      this.taskContent=areaValue;
      this.taskDeadLine=deadLine;
      alert(this.taskContent+" "+this.taskDeadLine);
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
