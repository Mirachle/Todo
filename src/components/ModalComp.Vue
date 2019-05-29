<template>
  <div :class="['modal-mask', 'animated', sendName]">
    <div class="modal-wrapper">
      <div class="modal-container">
        <div class="modal-header">
          <h3>{{title}}</h3>
        </div>

        <div class="modal-body">
          <div>
            <h6 class="left">Description:</h6>
          </div>

          <textarea v-model="currentValue"></textarea>

          <div>
            <p class="left">Deadline:</p>
          </div>
          <input type="time" v-model="myDate" style="width:100%; cursor: pointer;">
        </div>

        <div class="modal-footer" style="padding:5px 0px;border:none">
          <input type="button" @click="okEvent" value="Ok">
          <input type="button" @click="$emit('close')" value="Cancel">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalComp",
  props: ["title", "myDate", "currentValue", "sendName"],
  methods: {
    okEvent() {
      this.$emit("pressOkButton", this.currentValue, this.myDate);
    }
  }
};
</script>


<style scoped>
.modal-mask {
  position: fixed;
  z-index: 1;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;

}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 400px;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 4px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
  font-family: Helvetica, Arial, sans-serif;
}

.modal-header {
  border: none;
  padding: 0px;
  justify-content: center;
  margin-top: 0;
}

.modal-body {
  margin: 20px 0;
  padding: 0;
}

.modal-default-button {
  float: right;
}

textarea {
  width: 100%;
  resize: none;
}
input[type="button"] {
  background-color: rgb(7, 180, 248);
  border: 2px solid rgb(7, 180, 248);
  color: white;
  border-radius: 10%;
  transition-duration: 0.4s;
  cursor: pointer;
}

input[value="Ok"]:hover{
  background-color: white;
  color: black;
  border: 2px solid rgb(7, 180, 248);
}

input[value="Cancel"] {
  background-color: rgb(121, 120, 120);
  border: 2px solid rgb(121, 120, 120);
  color: white;
}

input[value="Cancel"]:hover {
  background-color: white;
  border: 2px solid rgb(121, 120, 120);
  color: black;
}

.left {
  margin-top: 5vh;
  text-align: left;
}
</style>
