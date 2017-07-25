<template>
  <div class="home">
      <div class="title-box">
          <input type="text" placeholder="影视 图书 唱片 小组等">
          <img src="../../assets/images/code.png" width="16" height="16" class="code-img">
          <img src="../../assets/images/search.png" width="20" height="20" class="search-img">
          <img src="../../assets/images/chat.png" width="24" height="24" class="chat-img">
      </div>
      <div v-if="active == 0">
          首页
      </div>
      <div v-if="active == 1">
          书影音
      </div>
      <div v-if="active == 2">
          广播
      </div>
      <div v-if="active == 3">
          小组
      </div>
      <div v-if="active == 4">
          我的
      </div>
      <div class="foot-box">
         <div class="foot-cell" @click="active=0">
             <img src="../../assets/images/index.png" width="24" height="24" v-if="active == 0">
             <img src="../../assets/images/index_nor.png" width="24" height="24" v-if="active != 0">
             <span :class="{'color-green':active==0}">首页</span>
         </div>
         <div class="foot-cell" @click="active=1">
             <img src="" width="24" height="24">
             <span :class="{'color-green':active==1}">书影音</span>
         </div>
         <div class="foot-cell" @click="active=2">
             <img src="" width="24" height="24">
             <span :class="{'color-green':active==2}">广播</span>
         </div>
         <div class="foot-cell" @click="active=3">
             <img src="" width="24" height="24">
             <span :class="{'color-green':active==3}">小组</span>
         </div>
         <div class="foot-cell" @click="active=4">
             <img src="" width="24" height="24">
             <span :class="{'color-green':active==4}">我的</span>
         </div>
      </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
        active:0
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
    .home{
        width: 100%;
        height:100%;
    }
    .title-box{
        z-index: 1000;
        height:3.5rem;
        background: #00CC33;
        position:relative;
        input[type="text"]{
            width:85%;
            box-sizing: border-box;
            text-align:center;
            font-size:.7em;
            height:2.5em;
            border-radius:4px;
            color:#6a6f77;
            -web-kit-appearance:none;
            -moz-appearance: none;
            display:block;
            outline:0;
            padding:0 1em;
            text-decoration:none;
            position:absolute;
            bottom:.4rem;
            left:.6rem;
        }
        input::placeholder { 
            color: #666; 
        } 
        .search-img{
            position:absolute;
            bottom:.6rem;
            left:.8rem;
        }
        .chat-img{
            position:absolute;
            bottom:.4rem;
            right:.6rem;
        }
        .code-img{
            position:absolute;
            bottom:.8rem;
            right:16%;
        }
    }
    .foot-box{
        z-index: 1000;
        position: absolute;
        bottom: 0;
        left: 0;
        display: flex;
        width: 100%;
        border-top:1px solid #CDCDCD; 
        .foot-cell{
            flex: 1;
            text-align:center;
            img{
                margin-top:.4rem;
            }
            span{
                display: block;
                margin-top:.2rem;
                margin-bottom:.1rem; 
                font-size:.5rem;  
            }
            .color-green{
                color: #00CC33;
            }
        }
    }
</style>
