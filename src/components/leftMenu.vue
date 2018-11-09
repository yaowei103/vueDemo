<template>
    <div class="leftMenu" father-component="App">
        <ul>
           
           <li v-for="item in leftMenuData1" :key="item.id" v-on:click="changeContainer(item)">
                <img :src="item.img">
                <span class="span-txt">{{item.txt}}</span>
                <span class="span-num"  v-if="item.num>0" >{{item.num}}</span>
            </li>
        </ul>
    </div>
</template>


<script>


export default {
  name: 'leftMenu',
  components:{},
  props:{
      liNum:{
        type:Number,
        require:true
      },
      id:{
        type:Number,
        require:true
      },
      leftMenuData:{
          type:Array,
          require:true
      }
  },
  data () {
    return {
        leftMenuData1:this.leftMenuData
    }
  },
  methods:{
      changeContainer:function(item){
          console.log('btn click',item)
          this.$emit('childChangeContainer',item);
      },
      reloadComponent:function(){
          debugger
          console.log('val___')
      }
  },
  watch :{
      leftMenuData1:'reloadComponent'
  }
}
</script>
<style>
.leftMenu{
    padding-top:15px;
}

.leftMenu ul li{
    text-align:center;
    position:relative;
    margin-bottom:20px;
}
.leftMenu ul li img{
     display:block;
     margin: 0 10px;
    
 }
.leftMenu ul li span.span-txt{
    font-size:7px;
    -webkit-text-size-adjust: none;
 }
.leftMenu ul li span.span-num{
    position:absolute;
    top:0;
    right:10px;
    color:#fff;
    background:#cc3300;
    border-radius:50%;
    font-size:12px;
    width:15px;
    height:15px;
 }
</style>