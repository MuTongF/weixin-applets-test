<template>
	<view>
		<!-- 轮播图 -->
		<uni-swiper-dot :info="info" :current="current" field="title"  color="#2e66c3" :mode="mode">
			<swiper class="swiper-box" @change="change" autoplay="true">
				<swiper-item v-for="(item ,index) in info" :key="index">
					<view class="swiper-item">
						<image style="width: 100%; background-color: #eeeeee;" mode="aspectFill" :src="item.content"></image>
					</view>
				</swiper-item>
			</swiper>
		</uni-swiper-dot>
	</view>
</template>

<script>
	import uniSwiperDot from "../../components/uni-swiper-dot/uni-swiper-dot.vue"
	export default {
		components: {
			uniSwiperDot
		},
		data() {
			return {
				info: [{
					content: 'https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=1493390342,3676083771&fm=26&gp=0.jpg',
					title: '小程序测试开始啦'
				}, {
					content: 'https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=1761013875,3888483061&fm=26&gp=0.jpg',
					title: '哈哈哈哈哈哈哈哈'
				}, {
					content: 'https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=2746120682,390938867&fm=26&gp=0.jpg',
					title: '6666666翻了'
				}],
				current: 0,
				mode: 'nav',
			}
		},
		methods: {
			change(e) {
				this.current = e.detail.current;
			}
		}
	}
</script>

<style>
	/* 轮播图栏位颜色 */
	.uni-swiper__dots-box {
		background-color: #3F536E80 !important;
	}
</style>
