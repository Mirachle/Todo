<template>
<div>
    <div v-for="(item,index) in list" :key="index">
        <list-item :item="item" :index="index" @deleteRequest="request" />
    </div>
</div>
</template>

<script>
import ListItem from '@/components/ListItem'
export default {
  name: 'ListComp',
  components:{
      "list-item" : ListItem
  },
  props:{
      list:{
          default: ["Teendő #1","Teendő #2","Teendő #3"]
      }
  },
  methods:{
      request(value){
          this.$emit("deleteItemName",value);
      }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


</style>
