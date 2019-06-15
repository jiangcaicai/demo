<template>
    <div class="box">
        <p class="title">近期最受期待</p>
        <div class="swiper-container coming">
            <ul class="swiper-wrapper">
                <li v-for="data in datalist" :key="data.id" class="swiper-slide">
                    <div class="photo-box">
                        <img :src="data.img | path">
                        <div class="heart"><i class="iconfont icon-xin"></i></div>
                        <div class="wish-bg"></div>
                        <span>{{data.wish}}人想看</span>
                    </div>
                    <h5>{{data.nm}}</h5>
                    <p>{{data.comingTitle | time}}</p>
                </li>
            </ul>
        </div>
    </div>
</template>
<script>
import axios from 'axios'
import Vue from 'vue'
import Swiper from 'swiper' //swiper js
import 'swiper/dist/css/swiper.min.css' //swiper css
Vue.filter('path',function(path){
    return path.replace('w.h','170.230')
})
Vue.filter('time',function(time){
   
    return time.slice(0,5)
})
export default {
    data(){
        return{
            datalist:[]
        }
    },
    mounted(){
        axios({
            url:'/ajax/mostExpected?ci=65&limit=10&offset=0&token='
        }).then(res=>{
            console.log('aa',res.data.coming)
            this.datalist=res.data.coming
        })
        
    },
    updated(){
        new Swiper('.coming', {
        slidesPerView: 3.5,
        spaceBetween: 5,
        freeMode: true,
      
    });
    }
}
</script>
<style src="../../assets/iconfont/iconfont.css"></style>
<style lang="scss" scoped>
    .box{
     width: 3.43rem;
     padding: 0.12rem 0 0.12rem 0.15rem;
     height: 1.92rem;
     overflow: hidden;
     p{
         font-size: 0.14rem;
         line-height: 0.19rem;
         margin-bottom: 0.12rem;
         color: #333;
    }
     ul{
         li{
             width: 0.85rem;
             margin-right: 0.1rem;
             .photo-box{
                 position: relative;
                 margin-bottom: 0.06rem;
                 img{
                     width: 0.85rem;
                     height: 1.15rem;
                }
                 .heart{
                     width: 0.28rem;
                     height: 0.28rem;
                     line-height: 0.26rem;
                     text-align: center;
                     background: rgba(61,63,71,.6);
                     border-bottom-right-radius: 0.1rem;
                     position: absolute;
                     top: 0;
                     left: 0;
                     i{
                         font-size: 0.13rem;
                         color: #c2c2c2;
                    }
                }
                 .wish-bg{
                     width: 0.85rem;
                     height: 0.35rem;
                     position: absolute;
                     bottom: 0;
                     background-image: linear-gradient(-180deg,rgba(77,77,77,0),#000);
                }
                 span{
                     position: absolute;
                     left: 0.04rem;
                     bottom: 0.02rem;
                     color: #faaf00;
                     font-size: 0.11rem;
                     font-weight: 600;
                }
            }
             h5{
                 margin-bottom: 0.03rem;
                 font-size: 0.13rem;
                 color: #222;
                 text-overflow: ellipsis;
                 overflow: hidden;
                 white-space: nowrap;
                 font-weight: 700;
            }
             p{
                 font-size: 0.12rem;
                 color: #999;
            }
        }
    }
}
 
</style>

