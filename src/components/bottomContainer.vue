<template>
  <div class="bottomContainer" father-component="App">
    <!--<shoppingCart v-bind:data="bottomContainerData"/>-->
    <div class="car">
        <div>
          <div class="icon-div">
            <i class="iconfont icon-gouwuche"></i>
            <span v-if="liNum>0">{{liNum}}</span>
          </div>
            <span class="price">{{bottomContainerData.price}}</span>
            <span class="ok">{{bottomContainerData.ok}}</span>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'bottomContainer',
   props:{
      liNum:{
        type:Number,
        require:true
      },
   },
  data () {
    return {
      bottomContainerData: {price:'购物车空空如也',ok:'选好了',num:'0'}
            
    }
  },
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.bottomContainer{
  
}
.car{
    position:relative;
    
    border-top:1px solid #ccc;
    
}
.car div{
    width:100%;
    display:flex;
    justify-content:flex-start;
}
.car img{
    width:40px;
    height:40px;
    line-height:40px;
    position:absolute;
    top:-20px;
    left:10px;
}
.car span.price{
    line-height:50px;
    flex-grow:1;
    text-align:left;
    padding-left:5px;
}
.car span.ok{
    line-height:50px;
    border-left:1px solid #ccc;
    background:#cc3300;
    width:100px;
    color:#fff;
}
.car div.icon-div{
  width:40px;
  height:40px;
  border:1px solid #333;
  border-radius:50%;
  align-items: center;
  justify-content: center;
  margin-top: -20px;
  margin-left: 10px;
  background: #fff;
  position:relative;
}
.car .icon-div i{
  font-size:30px;
  color:#ccc;
}
.icon-div span{
    position: absolute;
    top: 0;
    right: 0;
    color: #fff;
    background: #cc3300;
    border-radius: 50%;
    font-size: 12px;
    width: 15px;
    height: 15px;

}
</style>
