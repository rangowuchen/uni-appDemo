<template>
	<view>
		<view class="avatar">
			<image src="../../static/1.png" style="width: 100%; height: 100%;border-radius: 20px;" mode="aspectFit"></image>
			<!-- <img src="../../static/1.png" style="width: 100%;height: 100%;border-radius: 20px;" /> -->
		</view>
		<input type="number" v-model="telephone" class="btnClass" placeholder="请输入手机号" />
		<input password type="text" v-model="password" class="btnClass" placeholder="请输入密码" />
		<button type="primary" @click="loginTo" class="btnClass">登陆</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				telephone: "",
				password: ""
			};
		},
		methods: {
			loginTo() {
				console.log(this.telephone, this.password)
				if (this.telephone.length < 11) {
				    uni.showToast({
				        icon: 'none',
				        title: '手机号最短为 11 个字符'
				    });
				    return;
				}
				if (this.password.length < 6) {
				    uni.showToast({
				        icon: 'none',
				        title: '密码最短为 6 个字符'
				    });
				    return;
				}
				//navigateTo 不能直接写tab中的某一路径,否则会导致路径重复,导致页面不能跳转,报错
				//switchTab只能跳转到带有tab的页面，不能跳转到不带tab的页面
				uni.switchTab({
					url: "/pages/index/index"
				})
			}
		}
	}
</script>

<style>
	.avatar{
		margin: 0 auto;
		width: 180upx;
		height: 160upx;
		border-radius: 20px;
	}
	.btnClass {
		width: 650upx;
		margin: 100upx auto 0 auto;
	}
</style>
