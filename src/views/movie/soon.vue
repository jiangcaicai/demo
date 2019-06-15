<template>
    <div>
      <swiper></swiper>
        <ul>
            <li v-for="data in datalist" @click="handleChangepage()" :key="data.id">
            <p>{{data.comingTitle}}</p>
            <div class="box">
                <div class="photo">
                    <img :src="data.img | path"/>
                </div>  
                <div class="border-box">
                    <div class="content">
                        <div class="filmName">{{data.nm}}
                            <span v-if="data.preShow"><img src="../../assets/nowimg/ab.png" ></span>
                            <span v-if="data.version==='v2d imax'"><img src="../../assets/nowimg/2.png"></span>
                            <span v-if="data.version==='v3d'"><img src="../../assets/nowimg/3d.png"></span>
                            <span v-if="data.version==='v3d imax'"><img src="../../assets/nowimg/3dimax.png"></span>
                        </div>
                        <div class="wish">
                            <span class="person">{{data.wish}}</span>
                            <span class="p-person">人想看</span>
                        </div>
                            <div class="actor">主演: {{data.star}}</div>
                        <div class="time">{{data.rt}}上映</div>
                        <div class="button">
                            <span class="ys" v-if="data.showst===4">预售</span>
                            <span class="xk" v-if="data.showst===1">想看</span>
                            </div>
                        </div>
                    </div>     
                </div>
            </li>
        </ul>
    </div> 
</template>
<script>
import Vue from 'vue'
import axios from 'axios'
import swiper from './swiper'

Vue.filter('path',function(path){
        return path.replace('w.h','128.180')
    })

export default {
    
    data(){
        return{
            datalist:[]
        }
    },
    mounted ( ) {
        axios({
            url:'/ajax/comingList?ci=65&token=&limit=10'
        }).then(res=>{
            console.log(res.data.coming)
            this.datalist = res.data.coming
        })
    },
    methods:{
        handleChangepage (id) {
            this.$router.push(`/detail`)
        }
    },
    components:{
        swiper
    }
}
</script>
<style lang="scss" scoped>
    ul{
     width: 3.58rem;
     box-sizing: border-box;
     padding-top: 0.1rem;
     background: #f5f5f5;
     li{
         width: 100%;
         background: white;
         p{
             font-size: 0.14rem;
             color: #333;
             padding: 0.12rem 0.15rem 0 0.15rem;
        }
         .box{
             box-sizing: border-box;
             padding-left: 0.15rem;
             overflow: hidden;
             position: relative;
             .photo{
                 width: 0.64rem;
                 float: left;
                 box-sizing: border-box;
                 padding: 0.12rem 0rem;
                 img{
                     width: 0.64rem;
                     height: 0.9rem;
                }
            }
             .border-box{
                 float: left;
                 margin-left: 0.1rem;
                 width: 2.69rem;
                 border-bottom: 0.01rem solid #eeeded;
                 .content{
                     width: 2.02rem;
                     box-sizing: border-box;
                     padding: 0.12rem 0;
                     .filmName{
                         width: 100%;
                         height: 0.24rem;
                         line-height: 0.24rem;
                         font-size: 0.17rem;
                         color: #333;
                         font-weight: 700;
                         padding-right: 0.05rem;
                         margin-bottom: 0.03rem;
                         text-overflow: ellipsis;
                         overflow: hidden;
                         white-space: nowrap;
                         span{
                             display: inline-block;
                        }
                    }
                     .wish{
                         .person{
                             font-size: 0.15rem;
                             color: #faaf00;
                             font-weight: 600 
                        }
                         .p-person{
                             display: inline-block;
                             font-size: 0.13rem;
                             margin-left: 0.02rem;
                             color: #666;
                        }
                    }
                     .actor,.time{
                         overflow: hidden;
                         text-overflow:ellipsis;
                         white-space: nowrap;
                         font-size: 0.13rem;
                         color: #666;
                         margin-top: 0.03rem;
                    }
                     .button{
                         position: absolute;
                         top: 0.43rem;
                         right: 0.14rem;
                         span{
                             display: block;
                             width: 0.47rem;
                             height: 0.27rem;
                             cursor: pointer;
                             box-sizing: border-box;
                             border-radius: 0.04rem;
                             text-align: center;
                             color: #fff;
                             font-size: 0.12rem;
                             line-height: 0.27rem;
                        }
                         .ys{
                             background: #3c9fe6;
                        }
                         .xk{
                             background: #faaf00;
                        }
                    }
                }
            }
        }
    }
}
 
</style>
