<template>
<h1 :class="headerClass">{{headerText}}</h1>
</template>

<script>
export default {
  name: 'HeaderComp',
  props:{
      headerText:{
           type: String,
          default: "Todo"
      },
  },
  data(){
      return {
          headerClass: "todo-title"
      }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.todo-title{
    font-weight: 800;
    padding-bottom: 3%;
}

</style>
