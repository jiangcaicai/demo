<template>
    <div v-if="datalist" class="main">
        <div  class="title">
            <span @click="back"><i class="iconfont icon-zuojiantou"></i></span>
            <span>{{datalist.cinemaData.nm}}</span>
        </div>
        <div class="addr">
            <p>{{datalist.cinemaData.nm}}</p>
            <span>{{datalist.cinemaData.addr}}</span>
            <div>
                <img src="data:image/png;base64,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">
            </div>
            
        </div>
        <div class="swiper"  v-if="datalist">
            <swiper ref="swiper" class="shiyixia">
                <div class="swiper-slide" v-for="(data,index) in datalist.showData.movies" :key="data.id">
                        <img :src="handlePath(data.img)" @click="change(index)"/>         
                </div>
            </swiper>
          
           
        </div>
            <div class="information">
                <span>{{datalist.showData.movies[num].nm}}</span>
                <span v-if="datalist.showData.movies[num].sc!=='0.0'">{{datalist.showData.movies[num].sc}}<span>分</span></span>
                 <span v-if="datalist.showData.movies[num].sc==='0.0'&&datalist.showData.movies[num].globalReleased">暂无评分</span>
                 <span v-if="!datalist.showData.movies[num].globalReleased">{{datalist.showData.movies[num].wish}}<span>人想看</span></span>
                <p>{{datalist.showData.movies[num].desc}}</p>
            </div>
            <div class="date">
                <swiper ref="swiper" class="showdata">
                 <ul class="swiper-slide swiper-slide-active" v-for="(data,index) in datalist.showData.movies[num].shows" 
                    @click="changeColor(index)" :class="current===index?'active':''" :key="data.id">
                    <li>
                        {{data.dateShow}}
                    </li>
                </ul>
            </swiper>
                <!-- <ul>
                    <li v-for="(data,index) in datalist.showData.movies[num].shows" 
                    @click="changeColor(index)" :class="current===index?'active':''" :key="data.id">
                        {{data.dateShow}}
                    </li>
                </ul> -->
            </div>
            <div class="discount" v-if="datalist.showData.vipInfo">
                <span>{{datalist.showData.vipInfo[0].tag}}</span>
                <span>{{datalist.showData.vipInfo[0].title}}</span>
                <span>{{datalist.showData.vipInfo[0].process}}</span>
            </div>
            
            <div v-for="data,index in datalist.showData.movies[num].shows" v-show="number===index">
                <div v-if="data.plist.length===0" class="no">
                   <p>影片未上映</p>
                    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAJsAAACPCAMAAADa+FkzAAAAvVBMVEUAAADS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLR0dHS0tLS0tLS0tLS0tLR0dHS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLh4OD5+fnQ0ND7+/vi4eHS0tLf3t7j4uLd3d3U1NTY2Nj9/f3a2trNzc3c29vW1tbs6+vPz8/l5eXx8fH19PTp6enn5+fz8/Pu7u729vb///9UDtl1AAAAJHRSTlMA8q5wm7QkE/kxoz0c7N3IA9DnTGNUfNaSgUS5XQk4jCl2Z8CNGgAAAAAMnElEQVR42uyZ0ZabIBCG29729KIv0CuBGRAQEIlG8/6PVQoxaIzraXvsyUXHzWYTFL/9mWEY/PTp65dvn9/Pvn35EdE+I31Hw89fP31HdOr9zCF+/4SoxDuaQvyEtIbq/Qxq+p/tP9ue/Wd7E/vP9p/tA3trNogmosEveyc2AF5b5ZIpZWsO8BZs8eJa4bOpOrb8MzbOX5NxRT3KBoYxXKZpuoZxgEaip4pX8E/YeNUDf0FWS0MVtBNb29SCokbWFfwLtlZfxBMcwC8y3hPNGInG9C2aZr/+ZJr0HCMdwNlsvI0A3ZoNuDK0CvrGSDJNxg5EFyJWIr3pANQoDuey8TbecHhCs2hsBLmTMdIrNNHQhgxHYluw8TOcyMZfoVXKY08SWUYD713NuZUGW01mOtKjV2ew7aMBl74JLJMl/xJG8gp+maV01KUhNF5yOIEto5FnNMHRA8kBkA49GlnBo1c3sbklKYpcHLs0/wO2jMZXqqHpkmgPZ7O03F40ZiiKRuk6g8fKQcV32A7CoF5/h37QLJGxfASjxKJdqrkhe93gkR+oBmO/w/Z7aNIPaeIouvXeLtiEo1NuucPfBi/5x1P7GAP9kO04Qp3vdJZsvjfrVp0IRcNSt6hc592HurWEXYcjti1av0YDZfis1/z+zObodalbhCfcqH0JIpoO4mBMj1UTT1GYj9YsxxQcTivd4mtytBYfzARX+K04vaPxdTRJGnQRLL/pq3diOcNYstYtnhKorGBPgoK2x3YcBpVo0uzxrBvh5qEKCGXauSnjZZczjThC22c7RgPuFSmy3d+TKo8pDKxv5oaiW7xKeQ47aIIf5IXjCK3Amfb2uGfRj+ne03pOtPKqyVK3/Lq1xsGrCC1ox2zbCC2yGTuPZLJFQh3QS9U0jnoXMtpaN8aINRy28xorEbrDdqxa1qRPshV/KwIG7pBSdN2UBn2jWxSOqi2aLmjHbNsILUbVSraVWzF9aft+nNdNG93ioeiTBGPxtV224zDIXk47TdhWt5lDR5s5troR3VEL69FZq3bMxvvXaBVIeSl5KtpSt/JhrVuyu7IXKWGZDTa+dsS2CYPSgva++oivawhTwktHIVzrxsglhAthd16Lpd+NaodsfB8NLHb3Rc9VSESUPDD2kW6xI4XRVE90zrtoYWdAj9k478kOWgWOBpbnC0qlU05SKj7STV8bj1IpiV7leSVQB9sp95itFHv9Tg0v5ZTu3Bm0AJDq04qxPd10kF5xiMYVlSkLT1LCBu2YbT9CS/1Sp6zdUnlfgIvKmW6ZwtZxqowFyFW29SotTepU1/CqoB2xHaLls1Gk+zrK4bEsoXjRpabqurbk2M4rKKu+9E8QgfUvNriu0Y7ZeFd8bWvC0j7LpmARH6abM8WFp7zQzmOq6LIr6n7J2VMr0jQVOv6bNeC4j1aJxo+/2IDWqwxbZ6XYZI20taL30lkHdKuVPI6asNE34k/r066qjtis50s2VBNLLCIX8HXyrKRvs7zcxlT8d2z8Q7aQ2FZDldmyG+ZOG9PfcmZvFh1DYkvF4gn7lkKZq45sfK0bbe7LEOnunWYP1ON61aFoeyP6eh4bSwm7WXZhRJ7yr1Ku2S4Ol5ejvOoz2QJLELjKFeNtFZagzD0YuF8ETW1qRs4Z0xILhIFRAPfpzRo754HBO56+yYMcObDUEBwxXpxi4VS2SRlVCQAQVeNleGR7blA1zsjH3mDnI5yA+MOl6Rg5kc3SIQtyUQZtXddWGjfqkqM6Rz3ahJZAIpxRdTRljMhfDdSewJZzVoLTpJPGUG9Q5IQ1Z9PL2M7bvYlWjzadZ2zLElrKWac8+5Czb2l97TsQfdCl2Evzbd4mLyulW9qfHkZyY5nXynOey4DEqVQGLP8qy/KXa3L2OC/nNZRwDpuiY9EoVwGLemZdGxQ92WKFN1J1EpvFrmizrO9miabLRLReqzifWNbkJ7Cl3Lnc3VrrpskoGufq4arX9eGyaFTIq3PYhMTAdnTTF24MSkkNDoy91o0FlOIktqqmQuc7Peumr864mkdtLTUiwW1104LW5z0/RTexV7rpSZkGkuUcwF7oxiaHZzxru1deygw38sLf2PDIsZXgkgb2QrdbPGm//z9l49UgytbgVjc2SaygJDcvCNvoljcHd/rvjnXb3yxu5wVQf9v6mx6XSx+opHsRp7feqD20dmrhd9lKrR8yG0d50VvdBvr87GOjm74g5bC7Tx729smP0S7dPF4G2LO/bZ99YHjWjTEwVuyiXTpe/QnbckcWwPmWHev2k32z220VhgFwdXYzTXuFXY2TXwL5IQVR2Ps/1smSEzxOTmStF1Mu6qqiKg365NrY2M4CevsLOXnH2H87WXB9nK3smSxSwBqubsX9bTvX55XaT3pLmXylHr+C1nC28g+V4vQwZ5Ovgt6CLalOQuvGd1/9NAa0sKriCHIBNIStsAVAg4YWHY8kKLdItWSHm/qU+x6vkUI7q+zoXpE6eVVr9EADcYYdKWTOhJ2xkuXakjzHBToy4ypTJ9fIh7DhHgSicsiEeLoo4/qOsc4q06e8HLQmjapdf2b3xazC1uDmaoJF/ZOHWEK4UpyQUI06l/e7gMZq/T+MDXODEs55u4z0nPduwinl5Ey/fk8DtHd1tKtA2FC08uzg3UbPvaHwadljER30OdLN+UGgboazldGgXsfWxMv9A/KNCEjTMdONH7v0RDMEDWHDPbRcrIybfudpJOA7yOhIJ2dUj6DhbLjWSqPT3ujwO9AbHNMklzVedwja99lkXIpOMg6eDPJGowBflJsc4hRXBS3F0PvY9r3QWmVqkHC7zsnYxnFMJjevlpPK5CDiobi9sRVDy3SdVZwTZdk6bfNt3qaVWUU4VzaeRW/pd/npN4ZUtfvkM0k+uZwWjCHpw8/M0MYKW2+11kN42z4W3dDM5gfYgC8LY3gWLRqc2c621uA8eUZrcNY9o7U4h88SWot7BMQaPbTN/QtyC9Gg0b0VopOi2X0fQjz2pJzkwdaIRLZn7kTXngjHny8vnHPVngSql8vre6P7xN9fL5e3p18tytPb5SEP+dO+ue24CUNR9OQKuQEJuSeTW5HFAYwskPr/n1ZsE2aEfaBVW6kPXU/RLG+8Q0JyNAr/+c8fZ3cftzidv/rFvu3v1+BTB9eevPM6thc8H/AzhGsXDQbfFm8/Gw7QZH19++saLfnJrKm+99BkM3agl+0A8yxpkZU42Gl/87A0veDuXvuRi8KW35zranPkImlTlOhPoYeby5PYQsY3KuusUcSR6RPuqvJnxjPTRlGBhyVI9nLwsSwQOIEeJpilxM+R7kHlT1U14idB/kflfczsXjB1YqcbTvy6vdRPjubhltR/2sqVnAx8HsX2BbkbytOeEzrha0e+5KygFvSduB1xWtQdYTeA2SqPCDLcV1tjtTXRncnLYYwJtYAfAqDpOnYq2Blg4XZ0uwOcuvLyUp/Td3yWntPXLY0rzDv7m26xwvBxgkfZLUuVNPxnN3NBrOjvpq/vqMnLR+oved0taS2ofZLpbkUjjbzuJj9gDC/p67ZHrihFFsc6mYmSKzAEOH/6qPZJ4+cAd5Qyz5K0uYbeeUT5CXepF3w+tajI6wMMuruFE8XlwFDEaUWSIztMNDOAx1A/XDMso1QiONtcdOgFcJUPfBfLREmdX9cHld9Lz4tO582Ckrm+9uqroZ/pzmdlXsHZZbc0vRMOGZe+ZIftI2jJxZFh5XR+GDpmel6lNcjui75ORn7OFKcPuw9G2g+XNhtuWM0zsKafbu1XO/h1gqmCXqA9UX2pLZ1/+yX85y/w2I1aXGdf/WLb9l8vjyB8tewr/ID+fMPsauhHraZjjxls5s0b5TwcmP6wf29//cZM/O2XZtZ8c4lN5xtTe+OpinrIRdaiKNG7NbNmWbS94DhxlN4zzNu6yDnem1l1hbktf1k2o6pNewuA5QGFZZhsZsFwwLPI1EmOc6lfjNvSScme9Vm356NcTkRq+8I2qQq5/YkJudT8dhZ4rLKBj5nVVwe/VodeVdXs09rgATL/DTNTN3k4IrU9O4FHzix85QCExEwkdx8G8KTGvTiTY67Kx9RIdQnAWXHy8B6wPCWscEM185BzsDeFCU/IMXfyod6OGT2uLWHndoyywATVrcCXGlMjgnw1A59H5PP2HfWaJTGV38xgi2Q30d1tBDDv7rbu6zb+h7v9y+ft97oV31M7dbcoJdDdKBvX3ei87lYQ9ntRdSsLYaUodbdcEHDZDQlZiHe3vKDyqhu9PQNkJLgHmHT5G6yQtp7sNu/Oj7r0Dy5lJ1W1siDOAAAAAElFTkSuQmCC">
                </div>
                <div v-for="data in data.plist" class="buy" >
                    <div class="begin"> {{data.tm}}</div>
                    <div class="lang">{{data.lang}} {{data.tp}}</div>
                    <div class="price"><span>￥</span>{{(parseInt(data.vipPrice)+7)?(parseInt(data.vipPrice)+7):23}}</div>
                    <div class="vip" v-if="data.vipPriceName"><span> {{data.vipPriceName}}</span><span>￥{{data.vipPrice}}</span></div>
                    <div class="end">{{time(data.tm,data.dt)}} 散场</div>  
                    <div class="th">{{data.th}}</div>
                    <div class="extraDesc">{{data.extraDesc}}</div>
                    <div class="ticket">购票</div>
                </div>    
            </div>
            <div class="setmeal">
                <div class="tit">影院超值套餐</div>
                <div v-for="data in datalist.dealList.dealList" class="block">
                    <img :src="handlePath(data.imageUrl)">
                    <div class="top">
                        <span>{{people(data.recommendPersonNum)}}人</span>{{data.title}}
                    </div>
                    <div class="price">
                        <span>￥</span>{{data.price}}
                    </div>
                    <div class="curNumberDesc">{{data.curNumberDesc}}</div>
                    <div class="gobuy">去购买</div>
                    <div class="hot" v-if="data.cardTag">{{data.cardTag}}</div>
                </div>
            </div>
    </div>
</template>
<script>
import icon from '../../public/icon/iconfont.css'
import axios from 'axios'
import swiper from './studios/swiper'
export default {
    data(){
        return{
            datalist:null,
            num:0,
            current:0,
            number:0
        }
    },
    mounted(){
        this.$store.commit("TabbarMutation",false)
        axios(`/ajax/cinemaDetail?cinemaId=${this.$route.params.id}&movieId=883196`).then(res=>{            
            this.datalist = res.data 
        })
    },
    destroyed(){
			//显示tabbar
			// this.$store.state.isTabbarShow  = true;
			this.$store.commit("TabbarMutation",true)
		},
    components:{
        swiper,
    },
    methods:{
        back(){
            this.$router.go(-1)
        },
        people(recommendPersonNum){
            if(recommendPersonNum===1){
                return '单'
            }
            if(recommendPersonNum===2){
                return '双'
            }
            if(recommendPersonNum>2){
                return '多'
            }
        },
        time(tm,dt){
             var d = new Date(`${dt} ${tm}`)
            var date = d.getMinutes();
            d.setMinutes(date + this.datalist.showData.movies[this.num].dur)
            var hours = d.getHours()
            var minutes = d.getMinutes()
            hours = hours < 10 ? '0' + hours : hours;
            minutes = minutes < 10 ? '0' + minutes : minutes;              	
            return `${hours}:${minutes}`
        },
        handlePath(path){
        return path.replace('w.h','148.208');
        },
        change(index){
            this.num =index
            this.current = 0;
            this.number = 0;
            // 重新创建swiper
            // this.$router.push(`/studios/${id}`)
        },
        changeColor(index){
              this.current = index;
              this.number = index;                         
            },
        
    }
}
</script>
<style lang="scss" scoped>
.main{
     .addr{
         position: relative;
         padding: 0.15rem;
         p{
             font-size: 0.17rem;
             line-height: 0.24rem;
             font-weight: 700;
             color: #333;
        }
         span{
             display: block;
             margin-top: 0.02rem;
             font-size: 0.13rem;
             line-height: 18.0.05rem;
             color: #999;
             text-overflow:ellipsis;
             white-space:nowrap;
             overflow:hidden;
             width: 75%;
        }
         div{
             width:0.2rem;
             border-left: 0.01rem solid #eee;
             position: absolute;
             padding-left: 0.2rem;
             right: 0.2rem;
             top: 37%;
             img{
                 width: 0.22rem;
            }
        }
    }
     .no{
         text-align: center;
    }
     padding-bottom: 0.4rem;
     .tit{
         line-height: 0.45rem;
         height: 0.45rem;
         font-size: 0.15rem;
         color: #666;
         border-bottom: 0.01rem solid #eee;
    }
     .setmeal{
         padding-left: 0.15rem;
         .block{
             padding-bottom: 0.1rem;
             position: relative;
             overflow: hidden;
             border-bottom: 0.01rem solid #eee;
             margin: 0.1rem 0;
             .hot{
                 position: absolute;
                 left: 0;
                 top: 0rem;
                 height: 0.18rem;
                 line-height: 0.18rem;
                 background-color: #fa5939;
                 font-size: 0.12rem;
                 padding: 0 0.05rem;
                 color: #fff;
                 border-bottom-right-radius: 0.02rem;
            }
             img{
                 width: 0.92rem;
            }
             div{
                 position: absolute;
            }
             .top{
                 top: 0.02rem;
                 left: 1rem;
                 font-size: 0.14rem;
                 line-height: 0.18rem;
                 color: #333;
                 overflow: hidden;
                 text-overflow: ellipsis;
                 span{
                     display: inline-block;
                     vertical-align: top;
                     margin-top: 0.01rem;
                     margin-right: 0.07rem;
                     padding: 0 0.04rem;
                     font-size: 0.1rem;
                     line-height: 0.15rem;
                     height: 0.15rem;
                     background: #f90;
                     border-radius: 0.02rem;
                     color: #fff;
                }
            }
             .price{
                 top:0.7rem;
                 left: 1rem;
                 color: #f03d37;
                 font-size: 0.17rem;
                 span{
                     font-size: 0.12rem;
                }
            }
             .curNumberDesc{
                 bottom: 0.45rem;
                 right: 0.15rem;
                 line-height: 0.16rem;
                 height: 0.16rem;
                 font-size: 0.12rem;
                 color: #999;
            }
             .gobuy{
                 padding: 0 0.08rem;
                 height: 0.27rem;
                 line-height: 0.27rem;
                 font-size: 0.12rem;
                 border-radius: 0.03rem;
                 color: #fff;
                 background-color: #f03d37;
                 top: 0.65rem;
                 right: 0.15rem;
            }
        }
    }
}
 .buy{
     border-bottom: 0.01rem solid #eee;
     padding: 0.17rem 0;
     margin-left: 12.0.05rem;
     display: flex;
     flex-wrap: wrap;
     position: relative;
     height:0.35rem;
     .ticket{
         position: absolute;
         background: #f03d37;
         right: 0.15rem;
         top:30%;
         width: 0.5rem;
         height: 0.27rem;
         line-height: 0.28rem;
         font-size: 0.12rem;
         color: #fff;
         border-radius: 0.04rem;
         text-align: center;
    }
     .begin{
         position: absolute;
         font-size: 0.2rem;
         color: #333;
         line-height: 1;
         white-space: nowrap;
         margin-right: 0.43rem;
         left: 0.05rem;
         top: 0.07rem;
    }
     .lang{
         position: absolute;
         left: 0.75rem;
         top: 0.07rem;
         width: 0.9rem;
         margin-top: 0.02rem;
         line-height: 0.18rem;
         font-size: 0.13rem;
         color: #333;
         white-space: normal;
         margin-right: 0rem;
    }
     .price{
         position: absolute;
         left: 1.6rem;
         top: 0.07rem;
         line-height: 1;
         color: #f03d37;
         margin-top: 0.01rem;
         font-size: 0.19rem;
         span{
             font-size: 0.1rem;
        }
    }
     .vip{
         position: absolute;
         left: 1.95rem;
         top: 0.09rem;
         display: flex;
         margin-right: 0.5rem;
         align-items: center;
         span{
             display: block;
             line-height: 0.15rem;
             height: 0.15rem;
             -webkit-transform: scale(.8);
             transform: scale(.8);
             -webkit-transform-origin: left;
             transform-origin: left;
             margin-right: -0.08rem;
             border: 1px solid #ff9000;
             border-radius: 0.02rem;
             font-size: 0.12rem;
        }
         span:nth-of-type(1){
             color: #fff;
             background-color: #f90;
        }
         span:nth-of-type(2){
             color: #f90;
             background-color: #fff;
        }
    }
     .end,.th,.extraDesc{
         position: absolute;
         margin-top: 0.1rem;
         color: #999;
         font-size: 0.11rem;
         line-height: 1;
         white-space: nowrap;
         margin-right: 0.15rem;
         width: 0.8rem;
    }
     .end{
         top: 0.25rem;
         left: 0.05rem;
    }
     .th{
         margin-right: 0.1rem;
         white-space:normal;
         word-break:break-all;
         word-wrap:break-word;
         top: 0.25rem;
         left: 0.75rem;
    }
     .extraDesc{
         top: 0.25rem;
         left: 1.6rem;
    }
}
 .active{
     color: red;
     border-bottom: 0.02rem solid red;
}
 .discount{
     padding: 0 0.15rem;
     height: 0.42rem;
     line-height: 0.42rem;
     background-color: #fff5ea;
     span:nth-of-type(1){
         border-radius: 0.02rem;
         font-size: 0.1rem;
         line-height: 0.15rem;
         height: 0.15rem;
         width: 0.34rem;
         text-align: center;
         color: #fff;
         margin-top: 0.13rem;
         margin-right: 0.1rem;
         background-color: #ff941a;
    }
     span:nth-of-type(2){
         color: #fa9600;
         font-size: 0.12rem;
    }
     span:nth-of-type(3){
         line-height: 0.42rem;
         color: #999;
         font-size: 0.12rem;
         float: right;
    }
}
 .title{
     width: 100%;
     font-size: 0.18rem;
     font-weight: 400;
     text-align: center;
     line-height: 0.5rem;
     margin: 0 52.0.05rem 0 0;
     text-overflow: ellipsis;
     white-space: nowrap;
     overflow: hidden;
     color: #fff;
     background: #e54847;
     position: relative;
     span:nth-of-type(1){
         position: absolute;
         left:0.15rem;
         top:0.15rem;
    }
}
 .swiper{
     width: 100%;
     background-color: #40454d;
     .swiper-container {
     width: 100%;
     height: 100%;
}
 .swiper-container img{
     display: block;
     width: 0.85rem;
     height: 1.2rem;
}
 .swiper-slide {
     text-align: center;
     font-size: 0.18rem;
     background: #fff;
     display: -webkit-box;
     display: -ms-flexbox;
     display: -webkit-flex;
     display: flex;
     -webkit-box-pack: center;
     -ms-flex-pack: center;
     -webkit-justify-content: center;
     justify-content: center;
     -webkit-box-align: center;
     -ms-flex-align: center;
     -webkit-align-items: center;
     align-items: center;
     transition: 300ms;
}
 .swiper-slide:not(.swiper-slide-active){
     transform: scale(0.8);
}
}
 .information{
     padding: 0.05rem 0;
     background: white;
     text-align:center;
     span:nth-of-type(1){
         height: 0.24rem;
         line-height: 0.24rem;
         font-size: 0.17rem;
         color: #333;
         font-weight: 700;
         margin-right: 0.05rem;
    }
     span:nth-of-type(2){
         color: #ffb400;
         font-size: 0.16rem;
         span{
             font-size: 0.1rem;
             color: #ffb400;
        }
    }
     p{
         margin-top: 0.02rem;
         height: 18.0.05rem;
         line-height: 18.0.05rem;
         font-size: 0.13rem;
         color: #999;
    }
}
 .date{
     width: 100%;
     overflow: auto;
     background: rgba(0,0,0,0);
     .showdata{
         overflow: hidden;
        ul{
            width: 107px;
            text-align: center;
            float: left;
            margin-right: 30px;
            li{
                
                margin:0 0.05rem;
                height: 0.45rem;
                line-height: 0.45rem;
            }
        }
     }
     
}
 
 
</style>
