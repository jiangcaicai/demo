<template>
  <!-- ticket
    <ul>
      <router-link to='/detail/id'
                   tag='li'
                   activeClass="active">跳转详情页</router-link>
    </ul>
    <ul>
      <router-link to='/studios/id'
                   tag='li'
                   activeClass="active">跳转具体影城页</router-link>
    </ul> -->
  <div>
    <header class="Tnav">
      <div class="Tnav-left">
        <a href="#" @click="back"><i class="iconfont icon-zuojiantou"></i></a>
      </div>
      <h1 class="Tnav-header">{{datalist.nm}}</h1>
    </header>
    <div class="body">
      <div class="movie-detail">
        <div class="movie-filter"></div>
        <div class="poster-bg"></div>
        <div class="detail box-flex">
          <div class="poter">
            <img :src="path">
          </div>
          <div class="content flex">
            <div class="title middle line-ellipsis">{{datalist.nm}}</div>
            <div class="title-en-name line-ellipsis">{{datalist.enm}}</div>
            <div class="score line-ellipsis"
                 :style="{fontSize:checkType?'14px':'18px'}">{{ell}}
              <span class="snum"
                    v-show="isshowsc">{{arr}}</span>
            </div>
            <div class="type line-ellipsis">
              <span>{{datalist.cat}}</span>
              <div class="type-group"
                   v-if="datalist.version!='v3d imax'?false:true">
                <img style="width: 42px;"
                     class="sd-imax"
                     src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAGAAAAAeCAYAAADTsBuJAAAD+0lEQVRoge2aPUwUQRSAPy4YiZh4DbT8VJhIvA4KkyOhBq+Uyi2gFlssPAtoPW01cWm0RaxVTCi0EkOhFXe0WoiJGhJJ1uK9cefW/ZnF3K3R/ZLNDDNvfnhv5s3bvRkIggBgGLgIjACDlPSSE+AT8B74NhAEwXngCnCm0Gn9f/wAdgeBKf5O5T8regI9Ygi4DIwCUxXE7ZT0j2PgneZHKpQ+vwiONR2sFDqNEkoDFExpgIJx9f+TwDJwySprA0+A11bZCjCR0EcbeAp8zDnHKDWgBfj6oH/XgC3Np9EAVoE9TaNUtR+AJrCTMP4R4GkaZUv7iWvfhcsOmAQ2EOW/QZT+BlH0GjBtyU6o3L71gIRcC8B9YN5hzDSqQB0Yt8pqWtZ0aN9S2VpCfUPr68QbaE+fq4QLINr/VcQwO1mTcdkBS8A54B7w3CpfRHbFIqGiDU9i8tPALeAGshsOHMbOywVkVfoJ9Q1gLKMPo/RXiCLHgU6MzJzW2+PNIf/foZZn4rIDZoDvdCsfQtcz7DIQYqR1zS86tsnLF9J3QdyKtqkhL0mbhK7MS5D1dLwWYiTbdTWId02/4WKAReBaTPmspnl8+r7Kz2YJnpIWssIbMXVziFvZTGlvDOQjykxbyeYMuaCyW5q/qXVO5I2C5hGXtIG4n4/A45x9tBGX1gt8TeNWuqdpM6FtFTHcIaHv9hGDerEtpH4T2TV1JMjICgK6OK0BTDS0Tf6ophe+39BBFFJHVrxhHLiO+PVOQtsGsoJtBfqaeiljbiXknchrgDXEJd1CIiFzCOdhMqd8XpqaelbZaqQurZ1vlXUQo0WjLkPVkrfPA2eyDDCMRC+jkfJ9wpWS1wATyKHeKzqI0q4THo4e8gFsJ6HNHGF09BkIrKeu5XFuzfj9O3SfB85khaGTSOTSRsIrm2+I+4kaJ415lX+Ro81paAIvEaUc8btrieJpeo/46GVVZVYjZXXE2E0tayChaYvsiAvINsA+slonkJ1gx/tGmW2XgVR+RfvLe3DnZYcwgjnSvJ8gW0V2yyHJSqsiC9DTfmrAXcTteJach0RAN3QOmbvB5UXsgXa4jvj9AySMNJ8cHsa0WbLyxoWNIspf488/R7jQBB4RuogkPE3TdkiL0AAm5DRtO5bcEbIL3iKGGifjfcDFAM8Rd7OMvJTNaHkbUX70LRi6DdBGFL5t9dUPfMQIVdKVa1Z92mrtIGdIXeXGkGgrrs0eYvDbOoe4d5JfDARBsJAmEMMw/VHiv/qTpGEBTvc5ul8r+L+g/D2gYEoDFExpgIKpIDe1SvrLWU1PKsg1uZL+MUT4a9yn8mpicfwAdgf0cu555IpieTm395jLuR+Arz8BrLjpSMoYSlEAAAAASUVORK5CYII=">
              </div>
            </div>
            <div class="src line-ellipsis">{{datalist.src}}/{{datalist.episodeDur}}分钟</div>
            <div class="pubDesc line-ellipsis">{{datalist.pubDesc}}</div>
          </div>
        </div>
        <div class="arrow-g"
             @click="qiehuandetail()">
          <!-- 跳转详情页 -->
          <i class="iconfont icon-youjiantou"></i>
        </div>
      </div>
      <div id="showDays">
        <!-- <ticketdata :class="isShow?'min-line':''"
                    ref="swiper"></ticketdata> -->

        <ul id="timeline"
            :class="isShow?'min-line':''"
            ref="swiper1">
          <router-link to=''
                       tag='li'
                       :class="{active:current==index}"
                       v-for="(data,index) in time"
                       :key="data.item"
                       @click.native="handedata(index)"
                       ref="swiper">{{data}}</router-link>

        </ul>
      </div>
      <!-- <selection></selection> -->
      <!-- 中间导航栏————————待完成-->
      <!-- <div></div> -->
      <!-- 影院 -->
      <div class="cinema-list cinema">
        <div class="list-wrap"
             style="min-height: 503px;"
             v-infinite-scroll="zxloadMore"
             infinite-scroll-disabled="loading"
             infinite-scroll-immediate-check="false">
          <div class="item mb-line-b"
               v-for="(item,index) in filmes"
               :key="item.id" @click="handleChangePage(item.id)">
            <div class="title-block box-flex middle">
              <div class="title line-ellipsis">
                <span>{{filmes[index].nm}}</span>
                <span class="price-block">
                  <span class="price">{{filmes[index].sellPrice}}</span>
                  <span class="q">元起</span>
                </span>
              </div>
              <div class="location-block box-flex">
                <div class="flex line-ellipsis">{{filmes[index].addr}}</div>
                <div class="distance">{{filmes[index].distance}}</div>

              </div>
              <div class="flex"></div>
              <div class="label-block">
                <div class="allowRefund"
                     v-if="filmes[index].tag.allowRefund">退</div>
                <div class="endorse"
                     v-if="filmes[index].tag.endorse">改签</div>
                <div class="snack"
                     v-if="filmes[index].tag.snack">小吃</div>
                <div class="vipTag"
                     v-if="filmes[index].tag.vipTag">折扣卡</div>
                <div class="hallType"
                     v-for="datalie in filmes[index].tag.hallType"
                     :key="datalie">{{datalie}}</div>

              </div>
              <div class="discount-block">
                <div class="Tadd"
                     v-show="filmes[index].promotion.cardPromotionTag!=null?true:false">
                  <div class="discount-label normal card">
                    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAeCAYAAABNChwpAAAAAXNSR0IArs4c6QAAAgFJREFUSA3Nlz1LA0EQhmf3kouFEQwi+FEYQ+xEsImFoCDoL/CLaKd/QbC0sbCzFVuxsRS1jEVAsUqrIILRQAhaBGKMuawzwpGAm83mNhddCHfZnd3n3Z2ZuxsG2JI3YtQpVw6AiTkhYJj6/GqMwSsIdm312DsnMyzLCF79rGRAiIhfUOm6jL0FQvZU4Gfn0GU4KcINE5vjsc9LFXajE9kcfT7UDZaMQWwuG9Dpi/YyiIWZjqnSxrOAtWgANsYDysV1Bj0L0Flcx8ZoC1F0wf50UMo5fqjCY1FIxxo7jQSUHWgK+ag2YprfGwnIlQTQTk3a/46B2UEOIUu+v0gIIMgZLLTIZHJTOl+TL4K9ShckMc36Q+pc356QB6FLLJQFCqi4f39d2WoKLTy03ckg2OjAvcyXh9n1KX8eA0YC4n0MtuLoJru+o3bvjAS8o2vpfXCYsGEzZkFYHQ5SbcoglM5o6KQAoxhIDHBYiVqYERZcZB04f3aghNGv04wEuIDbQg3u8Lc4YsHymAVLeD17cuDypbWKjgggIZTpVwhM5x1YxzdlpaaXXB0T4J5GEbPy6F7/8WwUhC7U5OpZgIPfU5qnrNTn+UmoXLWNQc8n0AZDacqxUskpLXwcJDbHMinlI0O9NLI51WiAZZLa0odRZBKbU4FINRoDdtoNdxCDWMQk9jePWpE8hVOLbwAAAABJRU5ErkJggg=="
                         alt="">
                  </div>
                  <div class="discount-label-text">{{filmes[index].promotion.cardPromotionTag}}</div>
                </div>

              </div>
            </div>
            <div class="min-show-block  disabled  J-fload">
              <span>近期场次：</span>
              <span class="time-line">{{filmes[index].showTimes}}</span>

            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
// import selection from '../components/selection'
import icon from '../../public/icon/iconfont.css'
import axios from 'axios'
import { Indicator } from 'mint-ui'


export default {
  data () {
    return {
      datalist: {},//头部数据
      path: {}, //头部图片过滤
      arr: {},  //评论计算
      filmes: {}, //影院对象
      offset: 0,  //传给后端的影院值
      total: 56, //影院总长度
      isShow: false,
      time: [],   //日期对象
      current: 0, //加载数据需要的属性
      day: [],  //日期
      days: '', //获取点击日期
      today1: '', //获取今天日期
      isshowsc: true, //判断电影是否上映然后显示或者隐藏
      ell: '', //动态切换数据
      checkType: false, //动态切换font-size

    }
  },
  created () {
    //懒加载
    Indicator.open({
      text: '加载中...',
      spinnerType: 'fading-circle'
    });
    //片头请求
    axios({
      url: `/ajax/detailmovie?movieId=${this.$route.params.id}`,

    }).then(res => {
      this.path = this.$options.methods.handlePath(res.data.detailMovie.img)

      this.datalist = res.data.detailMovie
      let nodat = new Date()
      let a = nodat.getFullYear()
      let b = nodat.getMonth() + 1
      let c = nodat.getDate()
  
      if (b < 10) {
        b = '0' + b
      }
      let d = a + '-' + b + '-' + c
      if (res.data.detailMovie.rt > d) {
        this.isshowsc = false
        this.checkType = true
        this.ell = res.data.detailMovie.wish + '人想看'

      } else {
        this.checkType = false
        this.isshowsc = true
        this.ell = res.data.detailMovie.sc
        this.arr = this.$options.methods.sum(res.data.detailMovie.snum)

      }

      Indicator.close()
    })
  },

  mounted () {
  this.$store.commit("TabbarMutation",false)
    //懒加载
    Indicator.open({
      text: '加载中...',
      spinnerType: 'fading-circle'
    });

    //日期请求
    axios({
      method: 'post',
      url: '/ajax/movie?forceUpdate=1557386439279',
      data: {
        'movieId': this.$route.params.id,
        'day': '2019-05-10',
        'offset': '0',
        'limit': '20',
        'districtId': '-1',
        'lineId': '-1',
        'hallType': '-1',
        'brandId': '-1',
        'serviceId': ' -1',
        'areaId': '-1',
        'stationId': '-1',
        'updateShowDay': 'true',
        'reqId': '1557386661020',
        'cityId': '65'
      }
    }).then(res => {
      this.today1 =res.data.showDays.dates[0].date
      this.time = this.$options.methods.timedata(res.data.showDays.dates)
      for (let i = 0; i < res.data.showDays.dates.length; i++) {
        this.day.push(res.data.showDays.dates[i].date)
      }
      
//影院请求
    axios({
      method: 'post',
      url: '/ajax/movie?forceUpdate=1557459142350',

      data: {
        'movieId': this.$route.params.id,
        'day': this.today1,
        'offset': '0',
        'limit': '20',
        'districtId': '-1',
        'lineId': '-1',
        'hallType': '-1',
        'brandId': '-1',
        'serviceId': ' -1',
        'areaId': '-1',
        'stationId': '-1',
        'updateShowDay': 'true',
        'reqId': '1557459142180',
        'cityId': '65'
      }
    }).then(res => {
      this.filmes = res.data.cinemas
    })
    })
    
    window.onscroll = this.handScroll
  },
  destroyed () {
    window.onscroll = null
    this.$store.commit("TabbarMutation",true)
  },
    // components:{
    //     selection
    //   },
  methods: {
    back(){
            this.$router.go(-1)
        },
    handleChangePage (id) {
            this.$router.push(`/studios/${id}`)
        },
    //过滤方法
    handlePath (path) {
      return path.replace('w.h', '148.208');
    },
    //评论计算的方法
    sum (arr) {


      if (arr > 1000000) {
        arr = arr / 10000
        arr = Math.round(arr * 100) / 100 + ''
        arr = arr.slice(0, 5)
        return '(' + arr + '万人评' + ')'

      } if (arr > 100000) {
        arr = arr / 10000
        arr = Math.round(arr * 100) / 100 + ''
        arr = arr.slice(0, 4)
        return '(' + arr + '万人评' + ')'
      } else {
        arr = arr / 10000
        arr = Math.round(arr * 100) / 100 + ''
        arr = arr.slice(0, 3)
        return '(' + arr + '万人评' + ')'
      }



    },

    //滚动加载的方法 和 滚动请求
    zxloadMore () {
      if (this.filmes.length > 40 && this.filmes.length <= this.total) {
        return
      } else {
        this.offset += 20

      }
      Indicator.open({
        text: '加载中...',
        spinnerType: 'fading-circle'
      });
      axios({
        method: 'post',
        url: '/ajax/movie?forceUpdate=1557470548690',
        data: {
          'movieId': this.$route.params.id,
          'day': this.days,
          'offset': this.offset,
          'limit': '20',
          'districtId': '-1',
          'lineId': '-1',
          'hallType': '-1',
          'brandId': '-1',
          'serviceId': ' -1',
          'areaId': '-1',
          'stationId': '-1',
          'updateShowDay': 'true',
          'reqId': '1557470548682',
          'cityId': '65'
        },

      }).then(res => {
        this.filmes = [...this.filmes, ...res.data.cinemas]
        Indicator.close()
      })
      Indicator.close()
    },
    //详情页跳转
    qiehuandetail () {

    },
    //日期待完成...
    timedata (time) {
      // this.today1 = time[0].date //获取今天的日期 传给today 为了要那天的数据如果写死，则会在第二天返回空数据

      let time2 = []
      for (let i = 0; i < time.length; i++) {
        let a = time[i].date.slice(4, 5)
        let b = time[i].date.slice(7, 8)
        let c = time[i].date.slice(5, 7)
        let d = time[i].date.slice(8, 10)
        a = '月'
        b = '日'
        let f = c + a + d + b
        time2.push(f)
      }
      return time2
    },
    //点击特殊样式 和请求
    handedata (index) {
      this.current = index

      this.days = this.day[index]

      axios({
        method: 'post',
        url: '/ajax/movie?forceUpdate=1557486095840',
        data: {
          'movieId': this.$route.params.id,
          'day': this.days,
          'offset': '0',
          'limit': '20',
          'districtId': '-1',
          'lineId': '-1',
          'hallType': '-1',
          'brandId': '-1',
          'serviceId': '-1',
          'areaId': '-1',
          'stationId': '-1 ',
          'updateShowDay': 'false',
          'reqId': '1557484634327',
          'cityId': '65'
        }
      }).then(res => {
        this.filmes = res.data.cinemas

      })
    },

    //吸顶效果
    handScroll () {
      if ((document.documentElement.scrollTop || document.body.scrollTop) >= 200) {
        this.isShow = true
      } else {
        this.isShow = false
      }
    }


  }

}

</script>
<style lang="scss" scoped>
* {
     margin: 0;
     padding: 0;
}
 img {
     display: block;
}
 ul, li {
     list-style: none;
}
 a {
     text-decoration: none;
     cursor: pointer;
}
 .Tnav {
     height: 0.5rem;
     color: #fff;
     background: #e54847;
     border-bottom: 0.01rem solid #e54847;
     position: relative;
     font-family: Helvetica Neue, Helvetica, Arial, sans-serif;
     overflow: hidden;
     .Tnav-header {
         display: block;
         font-size: 0.18rem;
         -webkit-box-flex: 1;
         font-weight: 400;
         text-align: center;
         line-height: 0.5rem;
         margin: 0 0.8rem 0 0;
         text-overflow: ellipsis;
         white-space: nowrap;
         overflow: hidden;
         float: right;
         width: 2rem;
    }
     .Tnav-left {
         height: 0.5rem;
         line-height: 0.5rem;
         width: 0.5rem;
         float: left;
         a {
             height: 0.5rem;
             width: 0.22rem;
             line-height: 0.5rem;
             padding: 0 0.15rem;
             display: inline-block;
             .icon-zuojiantou {
                 display: inline-block;
                 width: 0.22rem;
                 height: 0.22rem;
                 vertical-align: middle;
                 position: relative;
            }
        }
    }
}
 //图片 
 .movie-detail {
     height: 1.88rem;
     cursor: pointer;
     .movie-filter {
         position: absolute;
         z-index: -1;
         width: 100%;
         height: 100%;
         background-color: #333;
    }
     .poster-bg {
         width: 100%;
         height: 100%;
         z-index: -1;
         overflow: hidden;
         position: absolute;
         -webkit-filter: blur(1.2rem);
         filter: blur(1.2rem);
         background-size: cover;
         background-repeat: no-repeat;
         opacity: 0.55;
    }
     .arrow-g {
         position: absolute;
         width: 0.1rem;
         right: 0.15rem;
         top: 50%;
    }
}
 .detail {
     height: 1.5rem;
     padding: 0.19rem 0.3rem 0.19rem 0.15rem;
     .poter img {
         width: 1.1rem;
         height: 1.5rem;
         box-sizing: border-box;
         display: inline-block;
    }
     .type-group {
         display: inline-block;
         width: 0.42rem;
         opacity: 0.85;
         margin-left: 0.05rem;
         img {
             display: block;
        }
    }
}
 .flex {
     flex: 1;
}
 .box-flex {
     display: flex;
}
 .content {
     overflow-x: hidden;
     margin-left: 0.12rem;
     line-height: 1;
     color: #fff;
     .title {
         font-size: 0.2rem;
         margin-top: 0.02rem;
         font-weight: 700;
         overflow: hidden;
    }
     .line-ellipsis {
         text-overflow: ellipsis;
         overflow: hidden;
         white-space: nowrap;
    }
     .score {
         font-size: 0.18rem;
         font-weight: 700;
         color: #fc0;
         margin-top: 0.11rem;
    }
     .snum, .type, .src, .title-en-name, .pubDesc {
         margin-top: 0.1rem;
         font-size: 0.12rem;
         color: #fff;
         opacity: 0.8;
    }
}
 #showDays {
     width: 100%;
     background-color: #fff;
     overflow-x: scroll;
     height: 0.45rem;
}
 .cinema-list .list-wrap {
     background-color: #fff;
     .item {
         padding: 0.13rem 0.15rem 0.13rem 0;
         margin-left: 0.15rem;
         background-color: #fff;
         overflow: hidden;
         border-bottom: 0.0.05rem rgb(155, 155, 155, 0.3) solid;
    }
     .title-block {
         display: block;
         .title {
             height: 0.23rem;
             line-height: 0.23rem;
             font-size: 0.16rem;
             color: #000;
             .price-block {
                 padding-top: 0.09rem;
                 padding-left: 0.03rem;
                 .price {
                     font-size: 0.18rem;
                     color: #f03d37;
                }
                 .q {
                     margin-left: 0.03rem;
                     color: #f03d37;
                     font-size: 0.11rem;
                }
            }
        }
         .location-block {
             margin-top: 0.06rem;
             font-size: 0.13rem;
             color: #666;
        }
         .label-block {
             height: 0.17rem;
             line-height: 0.17rem;
             margin-top: 0.04rem;
             margin-bottom: 0.04rem;
             overflow: hidden;
             font-size: 0;
             flex-shrink: 0;
             div {
                 position: relative;
                 display: inline-block;
                 padding: 0 0.03rem;
                 height: 0.15rem;
                 line-height: 0.15rem;
                 border-radius: 0.02rem;
                 font-size: 0.06rem;
            }
             div + div {
                 margin-left: 0.05rem;
            }
        }
         .discount-block {
             color: #999;
             margin-bottom: 0.04rem;
             .discount-label {
                 width: 0.15rem;
                 height: 0.14rem;
                 position: relative;
                 top: 0.03rem;
                 display: inline-block;
                 img {
                     width: 0.15rem;
                     height: 0.14rem;
                     display: inline-block;
                }
            }
        }
         .discount-label-text {
             margin-left: 0.03rem;
             font-size: 0.11rem;
             display: inline-block;
        }
    }
     .min-show-block {
         padding: 0 0.15rem 0 0;
         margin-right: -0.15rem;
         line-height: 1.5;
         font-size: 0;
         span {
             font-size: 0.12rem;
             color: #999;
        }
         .time-line {
             display: inline-block;
             
        }
    }
     .cinema-list .location-block, .cinema-list .price-block, .cinema-list .title-block {
         line-height: 1.5;
    }
     .line-ellipsis {
         text-overflow: ellipsis;
         overflow: hidden;
         white-space: nowrap;
    }
     .cinema-list .list-wrap .location-block .distance, .cinema-list .list-wrap .location-block .region {
         margin-left: 0.05rem;
    }
     .flex {
         flex: 1;
    }
     .endorse, .hallType, .allowRefund {
         color: #589daf;
         border: 1px solid #589daf;
    }
     .snack, .vipTag {
         color: #f90;
         border: 1px solid #f90;
    }
     .cinema-list .list-wrap .price-block .d, .cinema-list .list-wrap .price-block .price, .cinema-list .list-wrap .price-block .q {
         color: #f03d37;
    }
}
 .min-line {
     position: fixed;
     top: 0rem;
     left: 0rem;
     width: 100%;
     background-color: #fff;
     overflow-x: scroll;
     height: 0.45rem;
     white-space: nowrap;
     z-index: 100;
}
 .min-line::-webkit-scrollbar {
     display: none;
}
 #showDays #timeline {
     width: 100%;
     background-color: #fff;
     overflow-x: scroll;
     height: 0.45rem;
}
 //默认浏览器滚动条隐藏,有兼容问题 
 #timeline::-webkit-scrollbar {
     display: none;
}
 #timeline {
     padding: 0;
     margin: 0;
     white-space: nowrap;
}
 #timeline .active {
     border-bottom: 0.02rem solid #f03d37;
     color: #f03d37;
}
 #timeline li {
   
     display: inline-block;
     width: 1.15rem;
     line-height: 0.43rem;
     margin-left: 0.05rem;
     font-size: 0.14rem;
     text-align: center;
     list-style: none;
     color: #666;
}
 
</style>