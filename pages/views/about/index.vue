<template>
	<view class="content">
		<uni-nav-bar @clickLeft="back()">
			<view slot="left"><uni-icons type="back" size="20"></uni-icons>返回</view>
		</uni-nav-bar>

	</view>
</template>

<script>
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue"
	import uniIcons from "../../components/uni-icons/uni-icons.vue";
	export default {
		components: {
			uniNavBar,
			uniIcons
		},
		data() {
			return {
				title: '关于我'
			}
		},
		onLoad() {

		},
		methods: {
			back() {
				uni.switchTab({
					url:'../user/index'
				})
			}
		}
	}
</script>

<style>
	.uni-navbar__content_view{
		display: flex;
		margin-top: 18px;
		border: none;
	}
	.uni-navbar--border{
		border-bottom-style: none !important;
	}
	.title{
		text-align: center;
	}
</style>
