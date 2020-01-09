<template>
	<view class="content">
		<button type="primary" open-type="getUserInfo" @getuserinfo="getUserInfo">微信登录</button>

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
			getUserInfo:function (res1) {
				console.log("点击了登录")
				console.log(res1)
				const avatarUrl = res1.detail.userInfo.avatarUrl;
				console.log('用户头像：' + avatarUrl);
				const nickName = res1.detail.userInfo.nickName;
				console.log('用户昵称为：' + nickName);
				console.log('用户性别：' + (res1.detail.userInfo.gender == 1) ? '男' : '女');
				console.log('------------------------------');
				
				const user = {
					nickName:nickName,
					avatarUrl:avatarUrl,
					gender:res1.detail.userInfo.gender
				};
				uni.setStorage({
					key:'user',
					data:user,
					success() {
						// 存储登录成功
						
						uni.navigateBack({
							delta:1
						})
					},
					fail(e) {
						// 存储登录失败
						uni.showModal({
							title:'登录失败',
							showCancel:false,
							confirmText:'好的，知道了',
							content:"登录失败，请稍后重试"
						})
					}
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
