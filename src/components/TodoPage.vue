<template>
  <div class="card">
   <header-comp/>
   <input-row @changeValue="inputChangeValue"/>
   <filter-comp @filterType="filtered"/>
   <list-comp :filterName="filterType" :list="list" @deleteItemName="deletion" />
  </div>

</template>

<script>
import HeaderComp from '@/components/HeaderComp'
import InputRow from '@/components/InputRow'
import FilterComp from '@/components/FilterComp'
import ListComp from '@/components/ListComp'

export default {
  name: 'TodoPage',

  data(){
      return{
        list:[{isDone:false, text:"Teendő #1"},{isDone:false, text:"Teendő #2"},{isDone:false, text:"Teendő #3"}],
        filterType:""
      }
    },

  components:{
    'header-comp': HeaderComp,
    'input-row': InputRow,
    'filter-comp': FilterComp,
    'list-comp': ListComp
  },

  methods:{

    inputChangeValue(value){
      this.list.push({isDone:false, text:value})
    },

    deletion(value){
      this.list.splice(value,1)
    },

    filtered(value){
      this.filterType=value
    }
  }

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
