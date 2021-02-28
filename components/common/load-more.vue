<template>
	<view class="load-more">{{loadtext}}</view>
</template>

<script>
	export default{
		props:{
			loadtext:String,
		}
	}
</script>

<style scoped>
	.load-more{
		padding: 10upx;
		color: #aaa;
		text-align: center;
	}
</style>
