<template>
	<view class="content">
		<img :src="shareImage" class="share-image" />
		<canvasdrawer :painting="painting" class="canvasdrawer" @getImage="eventGetImage" />
		
		<button @click="eventDraw">绘制</button>
		
		
		
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				painting:{},
				shareImage:''
			}
		},
		onLoad() {

		},
		methods: {
eventDraw() {
				wx.showLoading({
					title: '绘制分享图片中',
					mask: true
				})
				this.painting = {
					width: 375,
					height: 555,
					clear: true,
					views: [{
							type: 'rect',
							background:'rgb(255,217,70)',
							url: 'https://hybrid.xiaoying.tv/miniprogram/viva-ad/1/1531103986231.jpeg',
							top: 0,
							left: 0,
							width: 375,
							height: 555
						},
						{
								type: 'rect',
								borderRadius:20,
								background:'#fff',
								lineWidth:6,
								strokeStyle:'#000',
								top: 100,
								left: 100,
								width: 200,
								height: 200
							},
						// {
						// 	type: 'image',
						// 	url: 'https://hybrid.xiaoying.tv/miniprogram/viva-ad/1/1531103986231.jpeg',
						// 	top: 0,
						// 	left: 0,
						// 	width: 375,
						// 	height: 555
						// },
						// {
						// 	type: 'image',
						// 	url: 'https://wx.qlogo.cn/mmopen/vi_32/DYAIOgq83epJEPdPqQVgv6D8bojGT4DrGXuEC4Oe0GXs5sMsN4GGpCegTUsBgL9SPJkN9UqC1s0iakjQpwd4h4A/132',
						// 	top: 27.5,
						// 	left: 29,
						// 	width: 55,
						// 	height: 55
						// },
						{
							type: 'image',
							borderRadius:22.5,
							lineWidth:4,
							strokeStyle:'#fff',
							url: 'https://tencentcos.yuchuantech.com/up/xiaoqingtou/9ffbcaa9-47c2-445e-b831-a73fda00699c.jpeg',
							top: 27.5,
							left: 29,
							width: 55,
							height: 55
						},
						{
							type: 'text',
							content: '您的好友【kuckboy】',
							fontSize: 16,
							color: '#402D16',
							textAlign: 'left',
							top: 33,
							left: 96,
							bolder: true
						},
						{
							type: 'text',
							content: '发现一件好货，邀请你一起0元免费拿！',
							fontSize: 15,
							color: '#563D20',
							textAlign: 'left',
							top: 59.5,
							left: 96
						},
						// {
						// 	type: 'image',
						// 	url: 'https://hybrid.xiaoying.tv/miniprogram/viva-ad/1/1531385366950.jpeg',
						// 	top: 136,
						// 	left: 42.5,
						// 	width: 290,
						// 	height: 186
						// },
						{
							type: 'image',
							url: 'https://hybrid.xiaoying.tv/miniprogram/viva-ad/1/1531385433625.jpeg',
							top: 443,
							left: 85,
							width: 68,
							height: 68
						},
						{
							type: 'text',
							content: '正品MAC魅可口红礼盒生日唇膏小辣椒Chili西柚情人',
							fontSize: 16,
							lineHeight: 21,
							color: '#383549',
							textAlign: 'left',
							top: 336,
							left: 44,
							width: 287,
							MaxLineNumber: 2,
							breakWord: true,
							bolder: true
						},
						{
							type: 'text',
							content: '￥0.00',
							fontSize: 19,
							color: '#E62004',
							textAlign: 'left',
							top: 387,
							left: 44.5,
							bolder: true
						},
						{
							type: 'text',
							content: '原价:￥138.00',
							fontSize: 13,
							color: '#7E7E8B',
							textAlign: 'left',
							top: 391,
							left: 110,
							textDecoration: 'line-through'
						},
						{
							type: 'text',
							content: '长按识别图中二维码帮我砍个价呗~',
							fontSize: 14,
							color: '#383549',
							textAlign: 'left',
							top: 460,
							left: 165.5,
							lineHeight: 20,
							MaxLineNumber: 2,
							breakWord: true,
							width: 125
						}
					]
				}

			},
			eventGetImage(event) {
				console.log(event)
				wx.hideLoading()
				const {
					tempFilePath,
					errMsg
				} = event.detail
				// if (errMsg === 'canvasdrawer:ok') {
				console.log(tempFilePath)
				this.shareImage = tempFilePath

				// }
			},
		}
	}
</script>

<style>
	.share-image{
		width: 500upx;
		height: 700upx;
	}
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
