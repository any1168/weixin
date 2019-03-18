<template>
  <view>
    <!-- 搜索框 -->
    <navigator url="/pages/search/main" hover-class="none" class="search">
      <view class="search_in">
        <icon type="search" size="30rpx" class="search_icon"/>搜索
      </view>
    </navigator>
    <!-- 轮播图 -->
    <swiper
      indicator-dots
      autoplay
      circular
      interval="4000"
      duration="1000"
      indicatorColor="rgba(255,255,255,.5)"
      indicatorActiveColor="#fff"
    >
      <block v-for="(item,index) in imgUrls" :key="index">
        <swiper-item>
          <image :src="item.image_src" class="slide-image" mode="aspectfill"></image>
        </swiper-item>
      </block>
    </swiper>
    <!-- 首页导航 -->
    <view class='pyg_nav'>
      <block v-for="(item,index) in navImage" :key="index">
       <image :src="item.image_src" mode="aspectfill"></image>
      </block>
    </view>
    <!-- 时尚女装 -->
    <view class='divide'></view>
      <image src="https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/pic_floor01_title.png" mode="aspectfill" class="pyg_Vogue"></image>
    <!-- 时尚女装内容 -->
    <view class='costume'>
      <view class='costume_left'>
        <image src="https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/pic_floor01_1@2x.png" mode="aspectfill"></image>
      </view>
      <view class='costume_right'>
        <image src="https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/pic_floor01_2@2x.png" mode="aspectfill"></image>
        <image src="https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/pic_floor01_3@2x.png" mode="aspectfill"></image>
        <image src="https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/pic_floor01_4@2x.png" mode="aspectfill"></image>
        <image src="https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/pic_floor01_5@2x.png" mode="aspectfill"></image>
      </view>
    </view>
      <!-- 户外运动 -->
    <view class='divide'></view>
      <image src="https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/pic_floor02_title.png" mode="aspectfill" class="pyg_Vogue"></image>
    <!-- 户外运动内容 -->
    <view class='costume'>
      <view class='costume_left'>
        <image src="https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/pic_floor02_1@2x.png" mode="aspectfill"></image>
      </view>
      <view class='costume_right'>
        <image src="https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/pic_floor02_2@2x.png" mode="aspectfill"></image>
        <image src="https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/pic_floor02_3@2x.png" mode="aspectfill"></image>
        <image src="https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/pic_floor02_4@2x.png" mode="aspectfill"></image>
        <image src="https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/pic_floor02_5@2x.png" mode="aspectfill"></image>
      </view>
    </view>
      <!-- 箱包配饰 -->
    <view class='divide'></view>
      <image src="https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/pic_floor03_title.png" mode="aspectfill" class="pyg_Vogue"></image>
      <!-- 箱包配饰内容 -->
    <view class='costume'>
      <view class='costume_left'>
        <image src="https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/pic_floor03_1@2x.png" mode="aspectfill"></image>
      </view>
      <view class='costume_right'>
        <image src="https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/pic_floor03_2@2x.png" mode="aspectfill"></image>
        <image src="https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/pic_floor03_3@2x.png" mode="aspectfill"></image>
        <image src="https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/pic_floor03_4@2x.png" mode="aspectfill"></image>
        <image src="https://lg-igjc8p1o-1256763078.cos.ap-shanghai.myqcloud.com/upload/pic_floor03_5@2x.png" mode="aspectfill"></image>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      //  轮播图数据
      imgUrls: [],
      // 首页导航数据
      navImage: []
      // 首页楼层头部图片
      // cate: []
    };
  },
  // onLoad 在小程序页面加载的时候触发一次
  onLoad() {
    // 请求轮播图数据
    wx.request({
      // 请求方式
      url: "https://www.zhengzhicheng.cn/api/public/v1/home/swiperdata",
      //  请求方式
      method: "GET",
      // 服务器返回数据
      success: res => {
        // console.log(res);
        this.imgUrls = res.data.message;
      }
    });
    // 请求首页分类数据
    wx.request({
      // 请求方式
      url: "https://www.zhengzhicheng.cn/api/public/v1/home/catitems",
      //  请求方式
      method: "GET",
      // 服务器返回数据
      success: res => {
        // console.log(res);
        this.navImage = res.data.message;
      }
    });
    // // 请求时尚女装数据
    // wx.request({
    //   // 请求方式
    //   url: "https://www.zhengzhicheng.cn/api/public/v1/home/floordata",
    //   //  请求方式
    //   method: "GET",
    //   // 服务器返回数据
    //   success: res => {
    //     console.log(res);
    //     this.cate = res.data.message;
    //   }
    // });
  }
};
</script>

<style>
.search {
  background-color: #eb4450;
  padding: 20rpx;
}
.search_in {
  height: 60rpx;
  color: #bdbdbd;
  background-color: #fff;
  border-radius: 10rpx;
  /* text-align: center;
  line-height: 60rpx; */
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 30rpx;
}
.search_icon {
  margin-right: 10rpx;
}
.slide-image {
  width: 750rpx;
  height: 340rpx;
}
swiper {
  height: 340rpx;
}
.pyg_nav {
  height: 190rpx;
  display: flex;
  align-items: center;
  justify-content: space-around;
}
.pyg_nav image {
  /* flex: 1; */
  width: 128rpx;
  height: 140rpx;
}
.pyg_Vogue {
  width: 750rpx;
  height: 59rpx;
  background-color: #f4f4f4;
}
/* 分割盒子 */
.divide {
  height: 20rpx;
  background-color: #f4f4f4;
}
.costume {
  display: flex;
  padding: 20rpx 0 20rpx 15rpx;
}
.costume_left image {
  width: 232rpx;
  height: 386rpx;
}
.costume_left {
  flex: 1;
}
.costume_right {
  flex: 2;
}
.costume_right image {
  width: 232rpx;
  height: 188rpx;
  margin-right: 10rpx;
}
</style>
