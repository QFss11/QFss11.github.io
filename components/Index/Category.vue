<template>
	<view class="category">
		<view class="category-item" :class="currentCategoryId==item.categoryId ? 'category-active':'' " v-for="item in categoryData" :key="item.categoryId" @click="changeCategoryFun(item.categoryId)">
			{{item.categoryName}}
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				currentCategoryId:1,
				categoryData: [
					{
						categoryId: 1,
						categoryName: '爆款1-2系'
					},
					{
						categoryId: 2,
						categoryName: '超值3系'
					},
					{
						categoryId: 3,
						categoryName: '品质4系'
					},
					{
						categoryId: 4,
						categoryName: '珍品5系'
					},
					{
						categoryId: 5,
						categoryName: '收藏6系'
					},
					{
						categoryId: 6,
						categoryName: '特级7系'
					},
					{
						categoryId: 7,
						categoryName: '豪华8系'
					},
					{
						categoryId: 8,
						categoryName: '传承9系'
					},
					{
						categoryId: 9,
						categoryName: '特别系列'
					},
					{
						categoryId: 10,
						categoryName: '限量系列'
					},
					{
						categoryId: 11,
						categoryName: '烈酒系列'
					}
				]
			}
		},
		methods:{
			// 
			changeCategoryFun(categoryId){
				let that = this
				// dom渲染后之前
				that.$nextTick(()=>{
					that.currentCategoryId = categoryId
					that.$bus.$emit('categoryEvent',{categoryId})
				})
				
			}
		},
		mounted() {
			console.log(1111)
			let that = this
			that.changeCategoryFun(1)
		}
	}
</script>

<style lang="scss" scoped>
	.category{
		width: 120px;
		height: 100%;
		font-size: 14px;
		background-color: #f3f3f3;
		overflow-y: auto;
	}

	.category::-webkit-scrollbar {
		width: 3px;
		/* 定义滚动条宽度 */
	}

	.category::-webkit-scrollbar-thumb {
		background-color: #888;
		border-radius: 6px;
	}

	.category::-webkit-scrollbar-track {
		background-color: #f1f1f1;
	}

	/* 定制 Firefox 中的滚动条样式 */
	.category {
		scrollbar-color: #888 #f1f1f1;
		/* thumb track */
		scrollbar-width: thin;
	}

	.category-item {
		width: 100%;
		text-align: center;
		padding: 15px 0;
		color: #282828;
	}

	.category-active {
		background-color: #ffffff;
		width: 100%;
		border-radius: 25px 0 0 25px;
		position: relative;
	}

	.category-active::after {
		content: "";
		position: absolute;
		border-radius: 50%;
		width: 8px;
		height: 8px;
		background-color: #d8314d;
		z-index: 9;
		top: 42%;
		left: 10px;
	}
</style>