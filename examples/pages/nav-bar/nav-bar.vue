<template>
    <view>
        <view class="uni-common-mt">
            本导航栏为自定义组件，并非原生导航栏。除非原生导航栏无法满足需求，否则不推荐使用自定义导航栏组件。具体参考http://ask.dcloud.net.cn/article/34921
        </view>
        <view class="example-title">基本用法</view>
        <uni-nav-bar left-icon="back" @click-left="back" title="标题"></uni-nav-bar>
        <view class="example-title">左右显示文字</view>
        <uni-nav-bar left-icon="back" right-text="菜单" left-text="返回" @click-left="back" title="标题"></uni-nav-bar>
        <view class="example-title">插入slot</view>
        <uni-nav-bar color="#333333" background-color="#FFFFFF" fixed="false" right-icon="scan" @click-left="showCity"
            @click-right="scan">
            <block slot="left">
                <view class="city">
                    <view>{{city}}</view>
                    <uni-icon type="arrowdown" color="#333333" size="22"></uni-icon>
                </view>
            </block>
            <view class="input-view">
                <uni-icon type="search" size="22" color="#666666"></uni-icon>
                <input confirm-type="search" @confirm="confirm" class="input" type="text" placeholder="输入搜索关键词" />
            </view>
        </uni-nav-bar>
    </view>
</template>

<script>
    export default {
        data() {
            return {
                city: '北京'
            }
        },
        methods: {
            back() {
                uni.navigateBack({
                    delta: 1
                })
            },
            showMenu() {
                uni.showToast({
                    title: '菜单'
                })
            },
            clickLeft() {
                uni.showToast({
                    title: '左侧按钮'
                })
            },
            search() {
                uni.showToast({
                    title: '搜索'
                })
            },
            showCity() {
                uni.showToast({
                    title: '选择城市'
                })
            },
            scan() {
                uni.showToast({
                    title: '扫码'
                })
            },
            confirm() {
                uni.showToast({
                    title: '搜索'
                })
            }
        },
        onPullDownRefresh() {
            console.log('onPullDownRefresh')
            setTimeout(function() {
                uni.stopPullDownRefresh()
                console.log('stopPullDownRefresh')
            }, 1000)
        }
    }
</script>

<style>
    .uni-common-mt{
        color: #7a7e83;
        font-size: 28upx;
        padding: 30upx;
    }
    .title {
        font-size: 15px;
        line-height: 20px;
        color: #333333;
        padding: 15px;
    }

    .city {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        width: 100%;
        margin-left: 8px;
		white-space: nowrap;
    }

    .input-view {
        width: 92%;
        display: flex;
        background-color: #e7e7e7;
        height: 30px;
        border-radius: 15px;
        padding: 0 4%;
        flex-wrap: nowrap;
        margin: 7px 0;
        line-height: 30px;
    }

    .input-view .uni-icon {
        line-height: 30px !important;
    }

    .input-view .input {
        height: 30px;
        line-height: 30px;
        width: 94%;
        padding: 0 3%;
    }
</style>
