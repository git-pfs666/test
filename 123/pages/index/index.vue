<template>
	<view class="wrap">
		<view class="state" :style="{height:stateHeight}"></view>
		<view class="header">
			<view class="left">
				<view class="imageBox">
					<image class="back" src="../../static/img/back.png"></image>
				</view>
				<view class="split"></view>
				<view class="imageBox">
					<image src="../../static/img/backIcon.png"></image>
				</view>
			</view>
			<view class="title">全部订单</view>
			<view class="right">
				
			</view>
		</view>
		<view class="nav">
			<view class="navItem" v-for="(item,index) in navItem" :key="index">
				<text :class="item.focus?item.navItemActive:''" @tap="changeNavItem(index)">{{item.text}}</text>
			</view>
		</view>
		<view class="content">
			<view class="each" :style="{height:item.data.length*450+'rpx'}" v-for="(item,index) in storeInfo" :key="index">
				<image v-if="item.show" class="rightTop" :src="item.title.stateImg"></image>
				<view v-else class="cacel">取消订单<image src="../../static/img/close.png"></image></view>
				<view class="title">
					<text>{{item.title.text}}</text>
				</view>
				<view style="margin-bottom: 30rpx;" v-for="(i,index) in item.data" :key="index">
					<view class="storeInfo">
						<image :src="i.img"></image>
						<view class="detail">
							<view class="storeName">{{i.info.name}}</view>
							<view class="time">
								<view class="start">{{i.info.startTime}}</view>
								<view class="OK">{{i.info.ok}}</view>
								<view class="pay">{{i.info.pay.success}}<text v-for="j in i.info.pay.text">{{j}}</text></view>
							</view>
						</view>
						<view class="price">{{i.price}}</view>
					</view>
					<view class="servicePrice">{{i.servicePrice}}</view>
					<view class="bottom">
						<view class="tips" v-show="i.tipe.show">{{i.tipe.text}}</view>
						<text class="againOrder" :style="{display:i.againOrder.display}">{{i.againOrder.text}}</text>
						<text class="share" :style="{color:i.share.color,border:'1px solid '+i.share.color}">{{i.share.text}}</text>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				navItem:[
					{
						text:'全部',
						navItemActive:'navItemActive',
						focus:true
					},{
						text:'待下单',
						navItemActive:'',
						focus:false
					},{
						text:'待结算',
						navItemActive:'',
						focus:false
					},{
						text:'已结算',
						navItemActive:'',
						focus:false
					},{
						text:'已作废',
						navItemActive:'',
						focus:false
					},
				],
				storeInfo:[
					{
						show:true,
						title:{
							icon:'',
							text:'cdf会员购背景',
							stateImg:'../../static/img/settlement.png'
						},
						data:[
							{
								img:'../../static/img/store1.png',
								info:{
									name:'肌肤之钥光凝前霜 37MLx2',
									startTime:'创建时间：2020-09-01 17:22:03',
									ok:'锁单时间：2020-09-01 17:22:03',
									pay:{
										success:'支付时间',
										fail:'作废时间',
										text:['去支付订单']
									}
								},
								price:'￥178.00',
								servicePrice:'服务费：187积分',
								againOrder:{
									text:'再来一单',
									display:'block',
									color:'rgb(170,170,170)'
								},
								share:{
									text:'分享得500积分',
									color:'rgb(241,178,160)'
								},
								tipe:{
									show:false,
									text:'下单时库存不足，请等待下次补货'
								}
							}
						]
					},{
						show:true,
						title:{
							icon:'',
							text:'cdf会员购背景',
							stateImg:'../../static/img/settlement.png'
						},
						data:[
							{
								img:'../../static/img/store1.png',
								info:{
									name:'肌肤之钥光凝前霜 37MLx2',
									startTime:'创建时间：2020-09-01 17:22:03',
									ok:'锁单时间：2020-09-01 17:22:03',
									pay:{
										success:'支付时间',
										fail:'作废时间',
										text:['去支付订单']
									}
								},
								price:'￥178.00',
								servicePrice:'服务费：187积分',
								againOrder:{
									text:'再来一单',
									display:'block',
									color:'rgb(170,170,170)'
								},
								share:{
									text:'分享得500积分',
									color:'rgb(241,178,160)'
								},
								tipe:{
									show:false,
									text:'下单时库存不足，请等待下次补货'
								}
							},{
								img:'../../static/img/store1.png',
								info:{
									name:'海蓝之谜La Mer 海蓝之谜终极愈颜水润系列 套装x2',
									startTime:'',
									ok:'锁单时间：2020-09-01 17:22:03',
									pay:{
										success:'支付时间',
										fail:'作废时间',
										text:['去支付订单']
									}
								},
								price:'￥178.00',
								servicePrice:'服务费：187积分',
								againOrder:{
									text:'再来一单',
									display:'block',
									color:'rgb(170,170,170)'
								},
								share:{
									text:'分享得500积分',
									color:'rgb(241,178,160)'
								},
								tipe:{
									show:false,
									text:'下单时库存不足，请等待下次补货'
								}
							}
						]
					},{
						show:false,
						title:{
							icon:'',
							text:'cdf会员购背景',
							stateImg:'../../static/img/settlement.png'
						},
						data:[
							{
								img:'../../static/img/store2.png',
								info:{
									name:'海蓝之谜La Mer 海蓝之谜终极愈颜水润系列 套装x2',
									startTime:'创建时间：2020-09-01 17:22:03',
									ok:'',
									pay:{
										success:'',
										fail:'',
										text:['仅限折扣才下单','总金额上限5000元']
									}
								},
								price:'￥1188.00',
								servicePrice:'服务费：187积分',
								againOrder:{
									text:'',
									display:'none',
									color:'rgb(170,170,170)'
								},
								share:{
									text:'支付订单',
									color:'rgb(241,178,160)'
								},
								tipe:{
									show:false,
									text:'下单时库存不足，请等待下次补货'
								}
							}
						]
					},{
						show:false,
						title:{
							icon:'',
							text:'cdf会员购背景',
							stateImg:'../../static/img/settlement.png'
						},
						data:[
							{
								img:'../../static/img/store1.png',
								info:{
									name:'海蓝之谜La Mer 海蓝之谜终极愈颜水润系列 套装x2',
									startTime:'创建时间：2020-09-01 17:22:03',
									ok:'',
									pay:{
										success:'',
										fail:'',
										text:['仅折扣才下单','总金额上限5000元']
									}
								},
								price:'￥178.00',
								servicePrice:'服务费：187积分',
								againOrder:{
									text:'',
									display:'none',
									color:'rgb(170,170,170)'
								},
								share:{
									text:'支付订单',
									color:'rgb(241,178,160)'
								},
								tipe:{
									show:false,
									text:'下单时库存不足，请等待下次补货'
								}
							},{
								img:'../../static/img/store3.png',
								info:{
									name:'海蓝之谜La Mer 海蓝之谜终极愈颜水润系列 套装x2',
									startTime:'',
									ok:'锁单时间：2020-09-01 17:22:03',
									pay:{
										success:'',
										fail:'',
										text:['仅限折扣才下单']
									}
								},
								price:'￥178.00',
								servicePrice:'服务费：187积分',
								againOrder:{
									text:'',
									display:'none',
									color:'rgb(170,170,170)'
								},
								share:{
									text:'删除订单',
									color:'rgb(170,170,170)'
								},
								tipe:{
									show:true,
									text:'下单时库存不足，请等待下次补货'
								}
							}
						]
					},{
						show:true,
						title:{
							icon:'',
							text:'cdf会员购背景',
							stateImg:'../../static/img/settlement.png'
						},
						data:[
							{
								img:'../../static/img/store4.png',
								info:{
									name:'科颜氏（kiehi’s）亚马逊白泥面膜125ML',
									startTime:'创建时间：2020-09-01 17:22:03',
									ok:'锁单时间：2020-09-01 17:22:03',
									pay:{
										success:'支付时间：2020-09-01 17:22:03',
										fail:'',
										text:[]
									}
								},
								price:'￥178.00',
								servicePrice:'服务费：187积分',
								againOrder:{
									text:'',
									display:'none',
									color:'rgb(170,170,170)'
								},
								share:{
									text:'再下一单',
									color:'rgb(241,178,160)'
								},
								tipe:{
									show:false,
									text:'下单时库存不足，请等待下次补货'
								}
							}
						]
					},{
						show:true,
						title:{
							icon:'',
							text:'cdf会员购背景',
							stateImg:'../../static/img/fail.png'
						},
						data:[
							{
								img:'../../static/img/store3.png',
								info:{
									name:'科颜氏（kiehi’s）亚马逊白泥面膜125ML',
									startTime:'创建时间：2020-09-01 17:22:03',
									ok:'锁单时间：2020-09-01 17:22:03',
									pay:{
										success:'作废时间：2020-09-01 17:22:03',
										fail:'',
										text:[]
									}
								},
								price:'￥178.00',
								servicePrice:'服务费：187积分',
								againOrder:{
									text:'',
									display:'none',
									color:'rgb(170,170,170)'
								},
								share:{
									text:'再下一单',
									color:'rgb(170,170,170)'
								},
								tipe:{
									show:false,
									text:'下单时库存不足，请等待下次补货'
								}
							}
						]
					}
				]
			}
		},
		computed:{
			stateHeight(){
				let temp;
				uni.getSystemInfo({
					success: (e) => {
						temp=e.statusBarHeight+'px'
					},
					fail:(e)=>{
						console.log(e)
					}
				})
				return temp;
			}
		},
		onLoad() {

		},
		methods: {
			changeNavItem(i){
				for(let j in this.navItem){
					this.navItem[j].focus=false
					this.navItem[j].navItemActive=''
				}
				this.navItem[i].focus=true
				this.navItem[i].navItemActive='navItemActive'
			}
		}
	}
</script>

<style lang="scss">
	*{
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}
	.wrap{
		width: 100%;
		height: auto;
		background-color: white;
		.state{
			width: 100%;
		}
		.header{
			width: 100%;
			height: 41px;
			position: relative;
			display: flex;
			align-items: center;
			.left{
				width: 20%;
				height: 60rpx;
				border: 1px solid rgb(220,220,220);
				border-radius: 50rpx;
				position: absolute;
				left: 20rpx;
				overflow: hidden;
				display: flex;
				.imageBox{
					flex: 1;
					text-align: center;
					.back{
						width: 20rpx;
					}
					image{
						width: 30rpx;
						height: 30rpx;
					}
				}
				.split{
					width: 2rpx;
					height: 80%;
					position: absolute;
					top: 10%;
					left: 50%;
					transform: translateX(-50%);
					background-color: rgb(170,170,170);
				}
			}
			.title{
				width: 100%;
				height: 100%;
				text-align: center;
				line-height: 41px;
			}
			.right{
				// @extend .left;
			}
		}
		.nav{
			width: 100%;
			height: 100rpx;
			display: flex;
			align-items: center;
			text-align: center;
			.navItem{
				flex: 1;
				.navItemActive{
					position: relative;
				}
				.navItemActive::after{
					content: '';
					position: absolute;
					bottom: -25rpx;
					height: 3px;
					border-radius: 20rpx;
					width: 100%;
					left: 0;
					background-color: red;
				}
			}
		}
		.content{
			width: 100%;
			height: auto;
			background-color: rgb(246,246,246);
			padding: 20rpx;
			.each{
				margin-bottom: 20rpx;
				padding: 0 30rpx 20rpx;
				width: 100%;
				height: 450rpx;
				background-color: white;
				border-radius: 20rpx;
				position: relative;
				.cacel{
					position: absolute;
					right: 50rpx;
					top: 0;
					font-size: 0.8rem;
					line-height: 100rpx;
					image{
						width: 25rpx;
						height: 25rpx;
						margin-left: 10rpx;
					}
				}
				.rightTop{
					position: absolute;
					width: 100rpx;
					height: 100rpx;
					right: 50rpx;
					top: -10rpx;
				}
				.title{
					width: 100%;
					height: 100rpx;
					line-height: 100rpx;
					vertical-align: middle;
					font-size: 0.8rem;
				}
				.storeInfo{
					width: 100%;
					height: 180rpx;
					display: flex;
					image,.price{
						width: 20%;
						height: 100%;
						font-size: 0.8rem;
						font-weight: bold;
						text-align: center;
					}
					image{
						width: 23%;
						border-radius: 20rpx;
						overflow: hidden;
					}
					.detail{
						padding-left: 20rpx;
						flex: 1;
						line-height: 45rpx;
						.storeName{
							width: 100%;
							height: auto;
							font-size: 0.8rem;
							word-break: break-word;
							font-weight: bold;
						}
						.time{
							width: 100%;
							height: auto;
							font-size: 0.7rem;
							overflow: hidden;
							text-overflow: ellipsis;
							white-space: nowrap;
							color: rgb(195,195,195);
							.pay{
								text{
									border-radius: 20rpx;
									padding: 0 10rpx;
									background-color: rgb(251,216,210);
									color: rgb(241,178,160);
								}
							}
						}
					}
				}
				.servicePrice{
					width: 100%;
					height: 40rpx;
					line-height: 40rpx;
					text-align: right;
					font-size: 0.7rem;
					line-height: 40rpx;
				}
				.bottom{
					width: 100%;
					height: 100rpx;
					font-size: 0.8rem;
					position: relative;
					.againOrder{
						position: absolute;
						top: 50%;
						transform: translateY(-50%);
						padding: 10rpx;
						border-radius: 30rpx;
						border: 1px solid rgb(170,170,170);
						color: rgb(170,170,170);
						right: 35%;
					}
					.share{
						right: 0;
						@extend  .againOrder;
						color: rgb(241,178,160);
						border: 1px solid rgb(241,178,160);
					}
					.tips{
						position: absolute;
						bottom: 0;
						color: rgb(238,118,0);
					}
				}
			}
		}
	}
</style>
