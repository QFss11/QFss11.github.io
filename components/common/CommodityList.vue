<template>
	<view class="commodityList">
		<!-- <image src="../../static/img/dirnks1.png" mode=""></image> -->
		<Commodity :commodity-data="filterSeriesData"></Commodity>
	</view>
</template>

<script>
	import Commodity from '@/components/common/Commodity.vue'
	export default {
		data() {
			return {
				categoryId:1,
				seriesData:[
					{
						id: 0,
						// 系列
						categoryId: 2,
						url: '../../static/img/dirnks1.png',
						name: '雷盛617西班牙千红',
						remark: '一箱四瓶',
						introduce: '这是产自西班牙的葡萄酒',
						vol: '13%vol',
						country: '西班牙',
						counttryIcon: '',
						price: 800.00,
						// 0 代表推荐,1代表热销
						hot: 0,
						num:1,
					},
					{
						id: 1,
						categoryId: 1,
						url: '../../static/img/dirnks1.png',
						name: '雷盛617西班牙千红',
						remark: '一箱四瓶',
						introduce: '这是产自西班牙的葡萄酒',
						vol: '13%vol',
						country: '美国',
						counttryIcon: '',
						price: 1800.00,
						// 0 代表推荐,1代表热销
						hot: 0,
						num:1,
					},
					{
						id: 2,
						categoryId: 4,
						url: '../../static/img/dirnks1.png',
						name: '雷盛617西班牙千红',
						remark: '一箱四瓶',
						introduce: '这是产自西班牙的葡萄酒',
						vol: '13%vol',
						country: '中国',
						counttryIcon: '',
						price: 600.00,
						// 0 代表推荐,1代表热销
						hot: 0,
						num:1,
					},
					{
						id: 3,
						categoryId: 1,
						url: '../../static/img/dirnks1.png',
						name: '雷盛617西班牙千红',
						remark: '一箱四瓶',
						introduce: '这是产自西班牙的葡萄酒',
						vol: '13%vol',
						country: '西班牙',
						counttryIcon: '',
						price: 700.00,
						// 0 代表推荐,1代表热销
						hot: 0,
						num:1,
					},
					{
						id: 4,
						categoryId: 8,
						url: '../../static/img/dirnks1.png',
						name: '雷盛617西班牙千红',
						remark: '一箱四瓶',
						introduce: '这是产自西班牙的葡萄酒',
						vol: '13%vol',
						country: '西班牙',
						counttryIcon: '',
						price: 900.00,
						// 0 代表推荐,1代表热销
						hot: 1,
						num:1,
					}
				],
			    filterSeriesData:[]
			}
		},
		components: {
			Commodity
		},
		methods:{		
		    changCategoryeFun(categoryId){
				console.log(categoryId)
				let that = this
				that.filterSeriesData = that.seriesData.filter(item=>item.categoryId == categoryId)
				console.log(that.filterSeriesData)
			}
		},
		mounted() {
			let that = this
			that.$bus.$on('categoryEvent', (res) => {
				that.changCategoryeFun(res.categoryId);
			});
		}
	}
    

</script>

<style>
	.commodityList{
		height: 100%;
		overflow-y: auto;
		padding-right: 30rpx;
	}
	/* #ifdef H5 */
	.commodityList::-webkit-scrollbar {
		width: 3px;
		/* 定义滚动条宽度 */
	}
	
	.commodityList::-webkit-scrollbar-thumb {
		background-color: #888;
		border-radius: 6px;
	}
	
	.commodityList::-webkit-scrollbar-track {
		background-color: #f1f1f1;
	}
	
	/* 定制 Firefox 中的滚动条样式 */
	.commodityList {
		scrollbar-color: #888 #f1f1f1;
		/* thumb track */
		scrollbar-width: thin;
	}
	/* #endif */
</style>