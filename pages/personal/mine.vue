<template>
	<view class="content">
		<view class="uni-list">
			<view class="uni-list-cell" hover-class="uni-list-cell-hover" @tap="bindLogo">
				<view class="uni-media-list uni-list-cell-navigate uni-navigate-right">
					<!-- <image class="uni-media-list-logo me-list-logo" :src="userImg"></image> -->
					<image class="uni-media-list-logo me-list-logo" src="../../static/1.png"></image>
					<view class="uni-media-list-body me-list-body">
						<view class="uni-media-list-text-top me-list-text">{{userName}}</view>
						<view class="uni-media-list-text-bottom uni-ellipsis me-list-bottom">手机号：12343212345</view>
					</view>
				</view>
			</view>
		</view>
		<!-- #ifdef APP-PLUS -->
		<view class="uni-list me-list">
			<view class="uni-list-cell" hover-class="uni-list-cell-hover" @tap="bindScan">
				<view class="uni-media-list uni-list-cell-navigate uni-navigate-right">
					<image class="uni-media-list-logo" src="../../static/saoyisao.png"></image>
					<view class="uni-media-list-body">
						<view class="uni-media-list-text-top me-list-setting">扫一扫</view>
					</view>
				</view> 
			</view>
		</view>
		<!-- #endif -->
		<view class="uni-list me-list">
			<view class="uni-list-cell" hover-class="uni-list-cell-hover" @tap="bindSetting">
				<view class="uni-media-list uni-list-cell-navigate uni-navigate-right">
					<image class="uni-media-list-logo" src="../../static/shezhi.png"></image>
					<view class="uni-media-list-body">
						<view class="uni-media-list-text-top me-list-setting">设置</view>
					</view>
				</view>
			</view>
		</view>
		<view class="uni-list me-list">
			<view class="uni-list-cell" hover-class="uni-list-cell-hover" @tap="bindCommicate">
				<view class="uni-media-list uni-list-cell-navigate uni-navigate-right">
					<image class="uni-media-list-logo" src="../../static/tongxinlu.png"></image>
					<view class="uni-media-list-body">
						<view class="uni-media-list-text-top me-list-setting">通讯录</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import {mapState} from 'vuex';
	
	
	export default {
		data() {
			return {				
			};
		},
		computed: mapState(['userName','userImg']),
		methods:{
			bindLogo(){
				uni.navigateTo({
					url:'./personal'
				});
			},
			bindScan(){
				uni.scanCode({
					onlyFromCamera: true,
					success: function (res) {
						console.log('条码类型：' + res.scanType);
						console.log('条码内容：' + res.result);
						console.log('path内容：' + res.path);
					}
				});
			},
			bindSetting(){
				uni.navigateTo({
					url:'./loginOut/loginOut'
				});
			},
			bindCommicate(){
				uni.navigateTo({
					url:'./contact/contact'
				});
			}
				
		}
	}
</script>

<style>
	page{
		background-color: #efeff4;
	}
	.me-list{
		margin-top: 40upx;
	}
	.uni-list:before{
		height: 0upx;
	}
	.uni-list:after {
		height: 0upx;
	}
	.uni-list-cell:after{
		height: 0upx;
	}
	.me-list-logo{
		width: 120upx;
		height: 120upx;
		border-radius: 15upx;
		margin-right: 30upx;
	}
	.me-list-body{
		height: 120upx;
	}
	.me-list-text{
		padding-top: 8upx;
		font-size: 1.2em;
		line-height: 1.2em;
		font-weight: bold;
	}
	.me-list-bottom{
		padding-bottom: 8upx;
		font-size: .8em;
		line-height: 1.2em;
	}
	
	.me-list-setting{
		font-size: 1em;
		line-height: 2.3em;
	}
</style>
