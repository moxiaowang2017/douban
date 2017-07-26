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
</style>
