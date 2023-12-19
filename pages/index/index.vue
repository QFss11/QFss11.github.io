<template>
	<view class="index">
		<Category></Category>
		<CommodityList></CommodityList>
	</view>
</template>


<script>
	import Category from '@/components/Index/Category.vue'
	import CommodityList from '@/components/common/CommodityList.vue'
	export default{
		components:{
			Category,
			CommodityList
		}
	}
</script>


<style lang="scss" scoped>
	.index{
		display: flex;
		width: 100vw;
		height: 100vh;
	}
</style>