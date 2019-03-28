<template>
<div>
    <div @click="itemClicked(item,index)" v-for="(item,index) in list"
        :key="index" style="display:inline-flex;padding:0 10px">
        <filter-list-item :item="item" :selected="cl(index)"/>
    </div>
</div>
</template>

<script>
import FilterListItem from '@/components/FilterListItem'
export default {
  name: 'FilterComp',
  components:{
      "filter-list-item": FilterListItem
  },
  props:{
        selected:{
            type: Boolean,
            required: true
        },
        item:{
            type:String,
            required: true
        }
  },
  data(){
        return{
            list: ["All","Pending","Done"],
            selectedIndex: undefined,
        }
    },
        methods:{
        itemClicked(value,index){
            this.selectedIndex=index
            this.selectItem=value
        },
        cl(index){
            return this.selectedIndex === index
        }
    },
    computed:{
        selectedItem(){
            if(this.selectedIndex === undefined){
                return "-"
            }
            return this.list[this.selectedIndex];

        }
    }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


</style>
