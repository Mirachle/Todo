<template>
<transition name="modal">
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
            <slot name="body">
              <textarea v-model="currentValue" rows="4" col="12"></textarea>
            </slot>
            <div>
              <p class="left">Deadline:</p>
            </div>
            <input type="datetime-local" v-model="myDate" style="width:100%" />
          </div>

          <div class="modal-footer" style="padding:5px 0px;border:none">
            <slot name="footer">
              <input type="button" @click="okEvent" value="OK" />
              <input type="button" @click="$emit('close')" value="Cancel" />
            </slot>
          </div>
        </div>
      </div>
    </div>
</transition>
</template>

<script>
export default {
  name: 'ModalComp',
  props:["title", "textAreaValue", "myDate", "currentValue", "sendName"],
  methods:{
    okEvent(){
      this.$emit('pressOkButton',this.currentValue,this.myDate)
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
  background-color: rgba(0, 0, 0, .5);
  display: table;
  transition: opacity .3s ease;
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
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
  transition: all .3s ease;
  font-family: Helvetica, Arial, sans-serif;
}

.modal-header h3 {
  margin-top: 0;
}

.modal-header{
  border:none;
  padding: 0px;
  justify-content: center;

}

.modal-body {
  margin: 20px 0;
  padding: 0;
}

.modal-default-button {
  float: right;
}

textarea{
  width: 100%;
  resize:none;
}
input[type=button]{
  background-color:rgb(7, 180, 248);
  border: none;
  color: white;
}

input[value="Cancel"]{
  background-color: rgb(121, 120, 120);
  border: none;
  color: white;
}

.left{
  text-align: left;
}

</style>
