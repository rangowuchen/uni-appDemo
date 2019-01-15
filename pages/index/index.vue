<template>
	<view class="index">
		<block v-for="(item, index) in list" :key="index">
			<view class="card" @click="goDetail(item)">
				<image class="card-img" :src="item.cover" mode="aspectFill"></image>
				<text class="card-num-view">{{item.img_num}}P</text>
				<view class="card-bottm row">
					<view class="car-title-view row">
						<text class="card-title">{{item.title}}</text>
					</view>
					<view @click.stop="share(item)" class="card-share-view">{{item.author_name}}</view>
				</view>
			</view>
		</block>
		<view class="loadMore" v-show="fetchPageNum!=3">加载中...</view>
	</view>
</template>

<script>
	import aa from '../../common/util.js'
	export default {
		data() {
			return {
				list: [],
				fetchPageNum: 1
			}
		},
		onLoad() {
			this.getData();
			console.log(aa.list)
		},
		onReachBottom() {
			console.log("滑动到页面底部")
			this.getData();
		},
		onPullDownRefresh() {
			console.log("下拉刷新");
			this.getData();
		},
		methods: {
			getData() {
				if (this.fetchPageNum == 1) {
					uni.stopPullDownRefresh()
					this.list = aa.list;
					this.fetchPageNum = 2;
					return;
				}
				if (this.fetchPageNum == 2) {
					this.list = this.list.concat(this.list);
					this.fetchPageNum += 1;
					return;
				}
				if (this.fetchPageNum == 3) {
					uni.showToast({
						title: "已经最新",
						icon: "none",
					})
					uni.stopPullDownRefresh();
					return;
				}
			},
			goDetail(e) {
				console.log(e)
				uni.navigateTo({
					url: "../index-detail/index-detail"
				})
			}
		}
	}
</script>

<style>

</style>
