<template>
 <input v-model="inputValue" @keyup.enter="$emit('changeValue',inputValue)" :type="inputType" :id="inputId">
</template>

<script>
export default {
  name: 'InputRow',
  data(){
      return{
        inputType: "text",
        inputId: "task-manager",
        inputValue: ""
      }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#task-manager{
    border: none;
    outline: none;
    padding: 12px 10px 12px 10px;
    border-radius: 5px;
    box-shadow: 0px 0px 10px 5px #bebebe;
    line-height: 1.4;
    margin-bottom: 5%;
}

</style>
