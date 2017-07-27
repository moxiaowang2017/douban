<template>
  <div class="index">
       <div class="carousel-wrap" id="carousel">
            <transition-group tag="ul" class='slide-ul' name="list">
                <li class="slide-li" v-for="(list,index) in slideList" :key="index" v-show="index===currentIndex" @mouseenter="stop" @mouseleave="go">
                    <a :href="list.clickUrl" >
                        <img :src="list.image" :alt="list.desc">
                    </a>
                </li>
            </transition-group>
            <div class="carousel-items">
                <span v-for="(item,index) in slideList.length" :class="{'active':index===currentIndex}" @mouseover="change(index)"></span>
            </div>
        </div>
        <div class="news-box">
            <div class="white-box"></div>
            <div class="title-box">热点</div>
            <div class="news-cells">
                <div class="news-left">
                    <span class="news-title">给自己订个小目标</span>
                    <span class="news-label">我问儿子省重点有没有希望，他沉吟半天说：“很难哎！没什么把握。”</span>
                    <span class="news-label-2">作者：风行水上</span>
                </div>
                <div class="news-right">
                    <img class="news-images"  src="../../assets/images/news-1.jpg">
                </div>
            </div>
            <div class="news-cells">
                <div class="news-left">
                    <span class="news-title">给大英百物展“找茬”：法老王变脸？刘易斯棋子少了几颗？</span>
                    <span class="news-label">木乃伊脸都绿了</span>
                    <span class="news-label-2">作者：辄馨</span>
                </div>
                <div class="news-right">
                    <img class="news-images"  src="../../assets/images/news-2.jpg">
                </div>
            </div>
        </div>
        <div class="timer-box">
            <div class="gray-box"></div>
            <div class="title-box">豆瓣时刻 <span class="more">更多专栏<img src="../../assets/images/more.png" width="24" height="24"></span></div>
            <div class="card-box">
                <div class="header-box"></div>
                <img class="person-images" src="" width="30" height="30">
                <span class="person-name">曾志荣</span>
                <span class="person-career">艺术策划人,美学普及者</span>
                <div class="content-box">

                </div>
            </div>
        </div>
  </div>
</template>

<script>
export default {
  data () {
     return {
         slideList: [
            {
                "clickUrl": "#",
                "desc": "nhwc",
                "image": require("../../assets/images/1.jpg")
            },
            {
                "clickUrl": "#",
                "desc": "hxrj",
                "image": require("../../assets/images/2.jpg")
            },
            {
                "clickUrl": "#",
                "desc": "rsdh",
                "image": require("../../assets/images/3.jpg")
            }
        ],
        currentIndex: 0,
        timer: ''
     }
  },
created() {
    //在DOM加载完成后，下个tick中开始轮播
    this.$nextTick(() => {
        this.timer = setInterval(() => {
            this.autoPlay()
        }, 4000)
    })
},
  methods:{
        go() {
            this.timer = setInterval(() => {
                this.autoPlay()
            }, 4000)
        },
        stop() {
            clearInterval(this.timer)
            this.timer = null
        },
        change(index) {
            this.currentIndex = index
        },
        autoPlay() {
            this.currentIndex++
            if (this.currentIndex > this.slideList.length - 1) {
                this.currentIndex = 0
            }
        }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
    .carousel-wrap {
        position: relative;
        height: 7rem;
        width: 100%;
        overflow: hidden;
        background-color: #fff;
    }
    .slide-ul {
        width: 100%;
        height: 100%;
        .slide-li{
            position: absolute;
            width: 100%;
            height: 100%;
            img {
                width: 100%;
                height: 100%;
            }
        }
    }
    .carousel-items {
        position: absolute;
        z-index: 10;
        top: 5.5rem;
        right:1.8rem;
        height:1rem;
        margin: 0 auto;
        text-align: center;
        font-size: 0;
        span {
            display: inline-block;
            height: .3rem;
            width: .3rem;
            border-radius:.15rem;
            margin: 0 3px;
            background-color: #b2b2b2;
            cursor: pointer;
        }
        .active {
            background-color: #fff;
        }
    }
    .list-enter-active {
        transition: all 1s ease;
        transform: translateX(0)
    }

    .list-leave-active {
        transition: all 1s ease;
        transform: translateX(-100%)
    }

    .list-enter {
        transform: translateX(100%)
    }

    .list-leave {
        transform: translateX(0)
    }
    .news-box{
        background: #fff;
        .white-box{
            height:1rem;
        }
        .title-box{
            height:1.2rem;
            line-height: 1.2rem;
            border-left:.3rem solid #ff8447; 
            color: #ff8447;
            padding-left:1rem; 
            font-size: 1rem;
        }
    }
    .news-cells{
         display: flex;
         border-bottom:1px solid #e5e5e5;
        .news-left{
            flex:3;
            span{
                display: block;
                padding:0 1.2rem;
            }
            .news-title{
                font-weight: bold;
                font-size: 1.1rem;
                margin-top:1rem;
                color:#474747; 
            }
            .news-label{
                margin-top:.75rem;
                color:#9b9b9b;
                font-size: .9rem;
            }
            .news-label-2{
                margin:1.2rem 0;
                color:#9b9b9b;
                font-size: .9rem;
            }
            
        }
        .news-right{
            flex:1;
            .news-images{
                margin-top:1rem; 
            }
        }
    }
    .timer-box{
        background: #f7f7f7;
        .gray-box{
            height: 1rem;
        }
        .title-box{
            height:1.2rem;
            line-height: 1.2rem;
            border-left:.3rem solid #42bd56; 
            color: #8b8b8b;
            padding-left:1rem; 
            font-size: 1rem;
            .more{
                margin-right:.7rem; 
                color:#b6b6b6;
                float:right;
                font-size:.8rem;
                img{
                    vertical-align:middle;
                }
            }
        }
    }
    .card-box{
        width: 70%;
        margin-left: 1.2rem;
        margin-top:1.2rem; 
        .header-box{
            position: relative;
            height:5rem;
            border-top-left-radius:.5rem;
            border-top-right-radius:.5rem;
            background:red;
        }
        .person-images{
            position: absolute;
            top:2rem;
            left:45%;
        }

    }
</style>
