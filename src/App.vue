<template>
  <div id="app">
    <div class="top">
      <leftMenu @childChangeContainer="changeContainer" :liNum="showLiNum" :id="showId" :leftMenuData="leftMenuData"/>
      <rightContainer @childAdd="add" :containerId="showContainerId" :containerTitle="showContainerTitle"/>
    </div>
    <div class="bottom">
      <bottomContainer @childAdd="add" :liNum="showLiNum"/>
    </div>
  </div>
</template>

<script>
// 
    // 
import leftMenu from './components/leftMenu'
import rightContainer from './components/rightContainer'
import bottomContainer from './components/bottomContainer'
export default {
  name: 'App',
  components:{leftMenu,rightContainer,bottomContainer},
  data(){
    return {
      showContainerId:11,
      showContainerTitle:'咖啡',
      showLiNum:0,
      showId:11,
      leftMenuData: [
            {id:11,img:require('./assets/1.jpg'),txt:'咖啡',num:'0'},
            {id:22,img:require('./assets/1.jpg'),txt:'饮料',num:'1'},
            {id:33,img:require('./assets/1.jpg'),txt:'面包',num:'0'},
            {id:44,img:require('./assets/1.jpg'),txt:'米饭',num:'0'},
            {id:55,img:require('./assets/1.jpg'),txt:'凉菜',num:'0'},
            {id:66,img:require('./assets/1.jpg'),txt:'稀饭',num:'0'},
            
      ],
    }
  },
  methods:{
    changeContainer:function(item){
      console.log('item.id',item.id);
      this.showContainerId = item.id;
      this.showContainerTitle = item.txt;
 
    },
    add:function(pageData){
      //以第二页为例
      var pageId = pageData.containerId;
      var pageDataList = pageData.containerList
      console.log('pageId',pageId);
      console.log('pageDataList',pageDataList);
      var total = 0;
      //循环计算及第二页一共应该显示数字几
      for(let i in pageDataList){
        total+=Number(pageDataList[i].number)
      }
      console.log('total',total)
      // //循环判断改变哪个菜单的num值
      var leftMenuData = this.leftMenuData;
      debugger
      for(let j in leftMenuData){
        if(leftMenuData[j].id == pageId){
          leftMenuData[j].num = total;
        }
      }
      
    }
  },

}
</script>

<style>
html,body{
   font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0px;
  padding:0;
  width:100%;
  height:100%;
  -webkit-text-size-adjust:none; 
}
#app {
  height:100%;
  display:flex;
  flex-direction:column;
}
.top{
  display:flex;
  flex-direction:row;
  flex-grow:1;
}
.bottom{
  display:fixed;
  bottom:0;
  left:0;
  width:100%;
  background:#fff;
  align-self:flex-end;

}
ul{
    padding:0;
    margin:0;
}
img{
    width:45px;
    height:45px;

}
li{
  list-style:none;
}


@font-face {font-family: "iconfont";
  src: url('//at.alicdn.com/t/font_908903_7kwykjjc8d3.eot?t=1541607293704'); /* IE9*/
  src: url('//at.alicdn.com/t/font_908903_7kwykjjc8d3.eot?t=1541607293704#iefix') format('embedded-opentype'), /* IE6-IE8 */
  url('data:application/x-font-woff;charset=utf-8;base64,d09GRgABAAAAAAUAAAsAAAAAB7gAAQAAAAAAAAAAAAAAAAAAAAAAAAAAAABHU1VCAAABCAAAADMAAABCsP6z7U9TLzIAAAE8AAAARAAAAFY8dkhnY21hcAAAAYAAAABfAAABnLQGHHNnbHlmAAAB4AAAAR8AAAFwY2G+3mhlYWQAAAMAAAAALwAAADYTMaT0aGhlYQAAAzAAAAAcAAAAJAfeA4VobXR4AAADTAAAAA4AAAAQEAAAAGxvY2EAAANcAAAACgAAAAoA5ABEbWF4cAAAA2gAAAAfAAAAIAERAF1uYW1lAAADiAAAAUUAAAJtPlT+fXBvc3QAAATQAAAAMAAAAElJxYFQeJxjYGRgYOBikGPQYWB0cfMJYeBgYGGAAJAMY05meiJQDMoDyrGAaQ4gZoOIAgCKIwNPAHicY2BkYWCcwMDKwMHUyXSGgYGhH0IzvmYwYuRgYGBiYGVmwAoC0lxTGByeMTwrZW7438AQw9zA0AAUZgTJAQDl1AxYeJztkMENgDAIRR+2msY4ikfjGt3Bkwt0ZdaoQD04hJ88Aj8/HABmIBm7kUFuBNdlroSfWMPPnLYXqwkUrdp6/04hiUSJq+JJWfi1RT/eLfnXBjHXgf9b24DpAVreFDoAeJxdTrtOw0AQ3L1LnJezwT7ju8Rg+/xKgWQky6RBSk2JhJSego4/gIpfoaOJRD4iHRI9JR9BgQznIKHAajWzI82OBhjA1ytf81MYgQQQOkTP6ukS6wU6S6x86RAmxT3vu0q5nx8G8RZlJnEHT79nc7VnAUAww9e4MbkmtfI9K9VJUS/+JD2rVJltrabHC38zPQ5AwyVAXoXMI5aUrF6y7r4QVYjWhFk9wlRLXR3uoks256nBs3pxjsYRoR8xvBHxlGgaF1FLET66iSJSSaZb0psgtJHbJyPLngdNn/C9dINmIGbukK8uJmLcmfnXQo55l7FO94FUnP885rEi9k9q8lU/u4tEEa7mXuAcxRPckieHYjpyB06PjjP4BroBMkAAeJxjYGRgYADiVz6q3+P5bb4ycLMwgMANToNaBP3/HAsDsz6Qy8HABBIFABaACSwAeJxjYGRgYG7438AQw8IAAkCSkQEVsAAARwoCbXicY2FgYGBBwgAAsAARAAAAAAAAACwARAC4AAB4nGNgZGBgYGEIZGBmAAEmIOYCQgaG/2A+AwAQ5AFvAHicZY9NTsMwEIVf+gekEqqoYIfkBWIBKP0Rq25YVGr3XXTfpk6bKokjx63UA3AejsAJOALcgDvwSCebNpbH37x5Y08A3OAHHo7fLfeRPVwyO3INF7gXrlN/EG6QX4SbaONVuEX9TdjHM6bCbXRheYPXuGL2hHdhDx18CNdwjU/hOvUv4Qb5W7iJO/wKt9Dx6sI+5l5XuI1HL/bHVi+cXqnlQcWhySKTOb+CmV7vkoWt0uqca1vEJlODoF9JU51pW91T7NdD5yIVWZOqCas6SYzKrdnq0AUb5/JRrxeJHoQm5Vhj/rbGAo5xBYUlDowxQhhkiMro6DtVZvSvsUPCXntWPc3ndFsU1P9zhQEC9M9cU7qy0nk6T4E9XxtSdXQrbsuelDSRXs1JErJCXta2VELqATZlV44RelzRiT8oZ0j/AAlabsgAAAB4nGNgYoAALgbsgIWRiZGZkYWRlYEjKzMRiPJ0OWEMQ470/NLy0uSMVAYGAKEdCdo=') format('woff'),
  url('//at.alicdn.com/t/font_908903_7kwykjjc8d3.ttf?t=1541607293704') format('truetype'), /* chrome, firefox, opera, Safari, Android, iOS 4.2+*/
  url('//at.alicdn.com/t/font_908903_7kwykjjc8d3.svg?t=1541607293704#iconfont') format('svg'); /* iOS 4.1- */
}

.iconfont {
  font-family:"iconfont" !important;
  font-size:16px;
  font-style:normal;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.icon-jiajian-:before { content: "\e64f"; }

.icon-jiajian-1:before { content: "\e675"; }

.icon-gouwuche:before { content: "\e600"; }

</style>
