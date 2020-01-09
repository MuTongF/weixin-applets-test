<template>
	<view class="content">

		<uni-list class="meun">
			<navigator url="/pages/views/about/index" open-type="redirect" hover-class="other-navigator-hover">
				<uni-list-item title="关于我" class="uni-list-item" :show-extra-icon="true" :extra-icon="{color: '#4cd964',size: '40',type: 'info'}"></uni-list-item>
			</navigator>
		</uni-list>
	</view>
</template>

<script>
	import uniList from "../../components/uni-list/uni-list.vue"
	import uniListItem from "../../components/uni-list-item/uni-list-item.vue"


	export default {
		components: {
			uniList,
			uniListItem
		},
		data() {
			return {
				title: '个人中心',
				userInfo: {
					avatarUrl: '',
					nickName: '',
					openId: '',
					gender: ''
				}
			}
		},
		onLoad() {
			// 小程序信息
			const accountInfo = uni.getAccountInfoSync();
			console.log(accountInfo);
			console.log("appId:" + accountInfo.miniProgram.appId); // 小程序 appId


			uni.login({
				provider: 'weixin',
				success: function(loginRes) {
					console.log(loginRes.authResult);
					// 获取用户信息
					uni.getUserInfo({
						provider: 'weixin',
						success: function(infoRes) {
							const avatarUrl = infoRes.userInfo.avatarUrl;
							console.log('用户头像：' + avatarUrl);
							const nickName = infoRes.userInfo.nickName;
							console.log('用户昵称为：' + nickName);
							const openid = infoRes.userInfo.openid;
							console.log('用户openId：' + openid);
							console.log('用户性别：' + (infoRes.userInfo.gender == 1) ? '男' : '女');
							console.log('------------------------------');
							console.log(infoRes.userInfo.sex);
							console.log(infoRes.userInfo.phonenumber);
							console.log(infoRes.userInfo.getUserInfo);
							this.userInfo.avatarUrl = avatarUrl;
							this.userInfo.nickName = nickName;
							this.userInfo.gender = infoRes.userInfo.gender;
							console.log(this.userInfo);
						}
					});
				}
			});

		},
		methods: {

		}
	}
</script>

<style>
	.content {
		margin-top: 5vw;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.uni-list-item {
		width: 100vw;
	}
	.uni-list-item text{
		font-size: 36rpx !important;
	}
	.meun{
		margin-top: 20vh;
	}
</style>
