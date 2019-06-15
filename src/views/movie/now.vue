<template>
    <div v-infinite-scroll="myLoadMore"
        infinite-scroll-immediate-check="false"
		infinite-scroll-disabled="loading">
       <ul v-for="data in datalist" @click="handleChangePage(data.id)" :key="data.id">
           <li class="fir">
               <img :src="data.img | path">
           </li>
           <li class="sec">
            <div class="h2">{{data.nm}}
                    <span v-if="data.preShow"><img src="../../assets/nowimg/ab.png" ></span>
                    <span v-if="data.version==='v2d imax'"><img src="../../assets/nowimg/2.png"></span>
                    <span v-if="data.version==='v3d'"><img src="../../assets/nowimg/3d.png"></span>
                    <span v-if="data.version==='v3d imax'"><img src="../../assets/nowimg/3dimax.png"></span>
            </div>
            <div class="score">
                <span v-if="data.sc===0 && data.showst===4">{{data.wish}}人想看</span>
                <span v-if="data.sc===0 && data.showst===3">暂无评分</span>
                <span v-if="data.sc!==0">观众评{{data.sc}}</span>
            </div>
               <p>主演：{{data.star}}</p>
               <p>{{data.showInfo}}</p> 
                <div class="btn">
                  <span class="buy" v-if="data.showst===3">购票</span>
                  <span class="order" v-if="data.showst===4">预约</span>
               </div>
           </li>
       </ul>
    </div>
</template>
<script type="text/javascript">
import axios from 'axios'
//import moviebar from './moviebar'
import Vue from 'vue'
Vue.filter('path',function(path){
    return path.replace('w.h','128.180')
})
export default {
    data () {
        return{
            datalist:[],
            movieIds:[],
            number:12
            //loading:false,
            //total:0,
            //current:1,
            //isShow:true,
            //isFixed:false
        }
    },
    mounted(){
        axios('/ajax/movieOnInfoList?token=').then(res=>{
            console.log(res.data.movieIds)
            this.movieIds = res.data.movieIds
            this.datalist=[...this.datalist,...res.data.movieList];
            //this.total = res.data.data.total
        })
    },

    destroyed(){
       
    },
    methods:{
        handleChangePage (id) {
            this.$router.push(`/ticket/${id}`)
        },
        myLoadMore(){
            
            
            this.loading = true;
            axios({
                url:`/ajax/moreComingList?token=&movieIds=${this.movieIds[this.number+0]}
                %2C${this.movieIds[this.number+1]}%2C${this.movieIds[this.number+2]}%2C${this.movieIds[this.number+3]}
                %2C${this.movieIds[this.number+4]}%2C${this.movieIds[this.number+5]}%2C${this.movieIds[this.number+6]}
                %2C${this.movieIds[this.number+7]}%2C${this.movieIds[this.number+8]}%2C${this.movieIds[this.number+9]}`
                }).then(res=>{
                    if(res.data.coming.length===0){
                        this.loading = true;
                        return;
                    }
                    this.number = this.number+10
            console.log(res.data.coming)
             this.datalist=[...this.datalist,...res.data.coming];
             this.loading = false;
        })
        }

    }
}
</script>
<style lang="scss" scoped>
   ul{
     position: relative;
     .fir{
         overflow:hidden;
         width: 0.64rem;
         height: 0.9rem;
         position: relative;
         margin-top: 0.12rem;
         margin-left: 0.12rem;
         float:left;
         img{
             background:#e1e1e1;
             height: 0.9rem;
             width: 0.64rem;
        }
    }
     .sec{
         padding: 0.12rem 0.15rem 0.12rem 0.12rem;
         margin-left: 0.74rem;
         margin-right: 0.3rem;
         height: 0.9rem;
         width: 2.1rem;
         position: relative;
         border-bottom: 0.01rem solid #eeeded;
         .h2{
             width: 100%;
             height: 0.24rem;
             line-height: 0.24rem;
             font-size: 0.15rem;
             color: #333;
             font-weight: 700;
             padding-right: 0.05rem;
             margin-bottom: 0.03rem;
             flex-shrink:1;
             text-overflow:ellipsis;
             overflow: hidden;
             white-space: nowrap;
             span{
                 display: inline-block;
            }
        }
         .score{
             span{
                 font-size: 0.13rem;
                 color: #666;
                 margin-top:0.06rem;
                 line-height: 0.15rem;
                 text-overflow:ellipsis;
                 overflow: hidden;
                 white-space: nowrap;
            }
        }
         p{
             font-size: 0.13rem;
             color: #666;
             margin-top:0.06rem;
             line-height: 0.15rem;
             text-overflow:ellipsis;
             overflow: hidden;
             white-space: nowrap;
        }
         .btn{
             position: absolute;
             top: 0.43rem;
             right: -0.35rem;
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
                 line-height: 0.28rem;
                 white-space: nowrap;
                 cursor: pointer;
            }
             .buy{
                 background:#f03d37;
            }
             .order{
                 background:#3c9fe6;
            }
        }
    }
}
 
</style>
