---
layout: post
title:  "微信小程序Grid九宫格"
date:   2020-02-28
categories: [blog, miniprogram]
---

    weui提供了小程序中使用的Grid组件（https://github.com/wechat-miniprogram/miniprogram-demo/tree/master/miniprogram/page/weui/example/grid）

wxml:
{% highlight html linenos %}
<view class="page">
    <view class="page__hd">
        <view class="page__title">小工具</view>
        <view class="page__desc">助你的瘦身一臂之力</view>
    </view>
  <view class="page__bd">
    <view class="weui-grids  bg-map">
    <block wx:for="{{grids}}" wx:key="*this">
                <navigator url="{{item.url}}" class="weui-grid" hover-class="weui-grid_active">
                    <image class="weui-grid__icon" src="{{item.imgPath}}" />
                    <view class="weui-grid__label">{{item.text}}</view>
                </navigator>
    </block>
    </view>
  </view>
</view>
{% endhighlight  %}

js:
{% highlight js linenos %}
// miniprogram/pages/functions/functions.js
Page({
  /**
   * 页面的初始数据
   */
  data: {
    grids: [{
      url: '/pages/add/add',
      imgPath: '../../images/weight.png',
      text:'体重记录'
    }, {
      url: '/pages/drinking/drinking',
        imgPath: '../../images/water.png',
        text: '喝水记录'
    },
    ]
  },
  /**
   * 生命周期函数--监听页面加载
   */
  onLoad: function(options) {
  },
  /**
   * 生命周期函数--监听页面初次渲染完成
   */
  onReady: function() {
  },
  /**
   * 生命周期函数--监听页面显示
   */
  onShow: function() {
  },
  /**
   * 生命周期函数--监听页面隐藏
   */
  onHide: function() {
  },
  /**
   * 生命周期函数--监听页面卸载
   */
  onUnload: function() {
  },
  /**
   * 页面相关事件处理函数--监听用户下拉动作
   */
  onPullDownRefresh: function() {
  },
  /**
   * 页面上拉触底事件的处理函数
   */
  onReachBottom: function() {
  },
  /**
   * 用户点击右上角分享
   */
  onShareAppMessage: function() {
  }
})
{% endhighlight %}

json:
{% highlight json linenos %}
{
  "usingComponents": {}
}
{% endhighlight %}

wxss:
{% highlight css linenos %}
/* miniprogram/pages/functions/functions.wxss */
@import '../common.wxss';
.bg-map{
    width: 90%;
    /* height: auto; */
    border-radius: 5px;
    box-shadow: rgba(5,26,180,0.15) 0px 1px 8px;
    margin: 16px 16px; 
    background: #fff;
    position: relative; 
}
{% endhighlight %}

效果图：
![微信小程序九宫格布局](/assets/images/wx-miniprogram-grid.png)

实际体验：
![瘦show](/assets/images/shoushow.jpg)