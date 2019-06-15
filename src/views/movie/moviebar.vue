<template>
    <div>
    <div class="header">猫眼电影</div>
    <div class="nav">
        <ul>
            <li>
                <span>大连</span>
                <i></i> 
            </li>
            <router-link to='/movie/now' tag='li' activeClass="active">正在热映</router-link>
            <router-link to='/movie/soon' tag='li' activeClass='active'>即将上映</router-link>
            <li class="nav-ico  iconfont iconsousuo" style="color:red"></li>
        </ul>
    </div> 
    </div>
</template>
<script>
export default {
    props:{
        myfixed:Function
    }
}
</script>

<style lang="scss" scoped>
div{
     width: 100%;
     .header{
         width: 100%;
         height: 0.5rem;
         color: white;
         background:#e54847;
         font-size: 0.18rem;
         font-weight: 400;
         text-align: center;
         line-height: 0.5rem;
         border-bottom: 0.01rem solid #e54847;
    }
     .nav{
         .nav-dre{
        }
         ul{
             display: flex;
             background: white;
             border:1px solid #e6e6e6;
             li{
                 flex:1;
                 height: 0.4rem;
                 line-height: 0.4rem;
                 text-align: center;
                 font-size: 0.15rem;
                 span{
                     white-space: nowrap;
                     overflow: hidden;
                     text-overflow:ellipsis;
                     max-width: 0.7rem;
                }
                 i{
                    /* margin-right: 0.05rem;
                     */
                     width: 0;
                     height: 0;
                     border:4px solid #b0b0b0;
                     border-left-color: transparent;
                     border-right-color: transparent;
                     border-bottom-color: transparent;
                     display:inline-block;
                     margin-left: 0.04rem;
                     margin-top: 0.05rem;
                     font-style: italic;
                }
            }
        }
    }
}
 .active{
     color: red;
     border-bottom:0.03rem solid red;
}
 
</style>
