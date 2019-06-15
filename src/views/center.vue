<template>
    <div class="top">
        <div class="title">
            <h1>我的</h1>
        </div>
        <div class="header">
            <img src="/img/3.jpg" alt="">
        </div>
        <div class="container">
            <div class="orders">
                <div class="title2">我的订单</div>
                <div class="list-two">
                     <div class="list-movie"><img src="/img/3.png" alt=""><a href="#"><p>电影</p></a></div>
                     <div class="list-store"><img src="/img/4.png" alt=""><a href="#"><p>商城</p></a></div>
                </div>
            </div>
            <div class="group">
                <div class="group1"><span>在线观影</span></div>
                <div class="group2"><span>优惠券</span></div>
                <div class="group3"><span>折扣卡</span></div>
            </div>
        </div>
    </div>
</template>


<style lang="scss" scoped>
    .top{
     background: #f3f3f3;
}
 .title {
     background:#e54847;
     height: 0.5rem;
     text-align: center;
     color: #ffffff;
     line-height: 0.5rem;
}
 .title h1 {
     font-size: 0.18rem;
}
 .header {
     width: 100%;
     height: 1.5rem;
     background: url(/img/5.png) no-repeat;
}
 .header img {
     display: inline-block;
     margin-top: 0.3rem;
     width: 0.6rem;
     height: 0.6rem;
     border-radius: 0.6rem;
     border: 3px solid #fff;
     margin-left: 41%;
}
 .container {
     font-size: 0.14rem;
     color: #777;
     height: 4.1rem;
}
 .orders {
     background: #fff;
     height: 1.49rem;
     margin-top: 0.1rem;
}
 .title2 {
     padding-top: 0.13rem;
     font-size: 0.15rem;
     line-height: 0.21rem;
     height: 0.21rem;
     color: #333;
     width: 0.8rem;
     margin: 0 auto;
}
 .list-two {
     display: flex;
}
 .list-movie {
     width: 50%;
     height: 0.97rem;
     margin-top: 0.18rem;
}
 .list-store {
     width: 50%;
     height: 0.97rem;
     margin-top: 0.18rem;
}
 .list-movie img {
     width: 0.4rem;
     height: 0.4rem;
     margin:0 auto;
     display: block;
}
 .list-movie p {
     margin-top: 0.1rem;
}
 .list-store img {
     width: 0.4rem;
     height: 0.4rem;
     margin:0 auto;
     display: block;
}
 .list-store p {
     margin-top: 0.1rem;
}
 .list-two a {
     color: #333;
     font-size: 0.15rem;
     text-decoration: none;
     text-align: center;
}
 .group {
     margin-top: 0.1rem;
     background: #fff;
     height: 1.32rem;
     color: #333;
}
 .group1 {
     height: 0.44rem;
     line-height: 0.44rem;
     font-size: 0.15rem;
     margin-left: 0.15rem;
     padding-right: 0.15rem;
     border-bottom: 0.0.05rem solid #f3f3f3;
}
 .group2 {
     height: 0.44rem;
     line-height: 0.44rem;
     font-size: 0.15rem;
     margin-left: 0.15rem;
     padding-right: 0.15rem;
     border-bottom: 0.0.05rem solid #f3f3f3;
}
 .group3 {
     height: 0.44rem;
     line-height: 0.44rem;
     font-size: 0.15rem;
     margin-left: 0.15rem;
     padding-right: 0.15rem;
     border-bottom: 0.0.05rem solid #f3f3f3;
}
 
</style>

