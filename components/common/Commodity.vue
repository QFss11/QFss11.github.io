<template>
	<view class="commodity">
		<view class="commodity-content" v-if="commodityData.length>0">
			<view class="commodity-item" v-for="(item,index) in commodityData" :key="index">
				<view class="commodity-left">
					<view :class="item.hot==0?'commodity-nohot':'commodity-hot'">
						{{item.hot==0?'推荐':'热销'}}
					</view>
					<image class="commodity-img" mode="" :src="item.url"></image>
					<view class="commodity-introduce">{{item.introduce}}</view>
				</view>
				<view class="commodity-right">
					<view class="commodity-name">
						{{item.name}}({{item.remark}})
					</view>
					<view class="commodity-tag-name">
						<view class="tag">{{item.vol}}</view>
						<view class="tag">{{item.country}}</view>
					</view>
					<view class="price-box">
						<view class="price">￥{{item.price}}</view>
						<view class="operation">
							<view class="add" @tap="addNumFun(item)"></view>
							<view class="num">{{item.num}}</view>
							<view class="sub" @tap="subNumFun(item)"></view>
						</view>
					</view>
				</view>
			</view>


		</view>
		<view v-else class="commodity-empty">
			<!-- <u-empty mode="car" 
			textSize="18"
			icon="http://cdn.uviewui.com/uview/empty/car.png" text="商品空空如也">
			</u-empty> -->
		</view>

	</view>

</template>

<script>
	export default {
		props: {
			commodityData: Array
		},
		data(){
			return{
				commodityList:[]
			}
		},
		mounted() {
			this.commodityList = this.commodityData
		},
		methods: {
			addNumFun(item) {
				if (item.num >= 99) {
					return
				}
				item.num++
			},
			subNumFun(item) {
				if (item.num <= 1) {
					return
				}
				item.num--
			}
		}
	}
</script>

<style scoped lang="scss">
	.commodity {
		width: 100%;
		height: 100%;
		.commodity-item {
			width: 100%;
			padding: 20px 0;
			display: flex;
			.commodity-left {
				width: 100px;
				position: relative;
			}
			
		}
		
	}

	.commodity-introduce{
		overflow: hidden;
		text-overflow: ellipsis;
		display: -webkit-box;
		-webkit-line-clamp:2;
		-webkit-box-orient:vertical;
		color:#333333;
		word-break: break-all;
		padding:6rpx 20rpx;
		font-size: 12px;
	}

	
	.commodity-nohot {
		position: absolute;
		background-color: #e5ab77;
		padding: 5px 8px;
		border-radius: 0px 10px 0 10px;
		top: 0;
		right: 0px;
		color: #fff;
		font-size: 12px;
		transform: scale(0.8);
	}

	.commodity-hot {
		position: absolute;
		background-color: #d8314d;
		padding: 5px 8px;
		border-radius: 0px 10px 0 10px;
		top: 0;
		right: 0px;
		color: #fff;
		font-size: 12px;
		transform: scale(0.8);
	}

	.commodity-img {
		width: 100px;
		height: 80px;
	}



	.seriesName {
		padding: 10px 0 0 20px;
		font-weight: bold;
		font-size: 14px;
		position: relative;
	}

	.seriesName::after {
		content: "";
		position: absolute;
		width: 3px;
		height: 15px;
		background-color: #d8314d;
		z-index: 9;
		top: 12px;
		left: 12px;
	}

	.commodity-name {
		font-size: 14px;
	}

	.commodity-tag-name {
		display: flex;
		margin: 5px 0;
	}

	.tag {
		padding: 5px;
		font-size: 12px;
		color: #6a6a6a;
		background-color: #f0f0f0;
		margin-right: 5px;
		border-radius: 5px;
	}

	.price-box {
		display: flex;
		justify-content: space-between;
		flex-wrap: nowrap;
	}

	.price {
		font-size: 14px;
		color: #d8314d;
	}

	.operation {
		display: flex;
		align-items: center;
	}

	.add,
	.sub {
		width: 20px;
		height: 20px;
		border-radius: 50%;
		background-color: #d8314d;
		position: relative;
		cursor: pointer;
	}

	.add::before {
		content: "";
		width: 2px;
		height: 15px;
		background-color: #fff;
		position: absolute;
		top: 3px;
		left: 45%;
	}

	.sub::after,
	.add::after {
		content: "";
		width: 2px;
		height: 15px;
		background-color: #fff;
		position: absolute;
		transform: rotate(90deg);
		top: 3px;
		left: 45%;
	}

	.num {
		margin: 0 5px;
	}

	.commodity-empty {
		display: flex;
		flex-direction: column;
		padding-left: 40rpx;
		padding-top: 40rpx;
	}
</style>