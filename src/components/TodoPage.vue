<template>
  <div class="card">
   <header-comp />
   <input-row @changeValue="inputChangeValue"/>
   <filter-comp/>
   <list-comp :list="list" @deleteItemName="deletion" />
   
  </div>

</template>

<script>
import HeaderComp from '@/components/HeaderComp'
import InputRow from '@/components/InputRow'
import FilterComp from '@/components/FilterComp'
import ListComp from '@/components/ListComp'

export default {
  name: 'TodoPage',
  components:{
    'header-comp': HeaderComp,
    'input-row': InputRow,
    'filter-comp': FilterComp,
    'list-comp': ListComp
  },
  props:{
    list:{
      default: ["Teendő #1","Teendő #2","Teendő #3"]
    }
  },
  methods:{
    inputChangeValue(value){
      this.list.push(value)
    },
    deletion(value){
    this.list.splice(value,1)
  }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scope>


.card{
  margin: 8% 20% 0% 20%;
  vertical-align: center;
  border: none;
  background-color: #e0e0e0;
}

</style>
