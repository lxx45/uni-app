<template>
	<view>
		<!-- 自定义导航 -->
		<uni-nav-bar  :statusBar="true" @clickRight="oppenAdd" :fixed="true">
			<!-- 左边 -->
			<block slot="left">
				<view class="nav-left">
					<view class=" icon iconfont icon-qiandao"></view>
				</view>
			</block>
			<!-- 中间 -->
			<view class="u-f-ajc nav-tab-bar">
				<block v-for="(tab,index) in tabBars" :key="tab.id">
					<view class="u-f-ajc" :class="{'active' :tabIndex==index}" @tap="changeTab(index)">
						{{tab.name}}
						<view class="nav-tab-bar-line" v-if="(tabIndex == index)"></view>
					</view>
				</block>
			</view>
			<!-- 右边 -->
			<block slot="right">
				<view class="nav-right u-f-ajc">
					<view class="icon iconfont icon-bianji1"></view>
				</view>
			</block>
		</uni-nav-bar>
		
		<!-- 列表 -->
		<block v-for="(item,index) in list" :key="index">
			<common-list :item="item" :index="index"></common-list>
			
		</block>
	</view>
</template>

<script>
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue";
	import commonList from "../../components/common/common-list.vue";
	export default {
		components: {
			uniNavBar,
			commonList
		},
		data() {
			return {
				tabIndex: 0,
				tabBars: [{
						name: "关注",
						id: "guanzhu"
					},
					{
						name: "话题",
						id: "topic"
					},
					
				],
				list:[
					// 文字
					{
						userpic:"../../static/demo/userpic/12.jpg",
						username:"哈哈",
						sex:0, //0 男 1 女
						age:25,
						isguanzhu:false,
						title:"我是标题",
						titlepic:"",
						video:false,
						share:false,
						path:"深圳 龙岗",
						sharenum:20,
						commentnum:30,
						goodnum:20
					},
					// 图文
					{
						userpic:"../../static/demo/userpic/12.jpg",
						username:"洋葱头",
						sex:1, //0 男 1 女
						age:20,
						isguanzhu:false,
						title:"我是标题",
						titlepic:"../../static/demo/datapic/13.jpg",
						video:false,
						share:false,
						path:"深圳 龙岗",
						sharenum:20,
						commentnum:30,
						goodnum:20
					},
					// 视频
					{
						userpic:"../../static/demo/userpic/12.jpg",
						username:"哈哈",
						sex:0, //0 男 1 女
						age:25,
						isguanzhu:false,
						title:"我是标题",
						titlepic:"../../static/demo/datapic/13.jpg",
						video:{
							looknum:"20w",
							long:"2:47"
						},
						share:false,
						path:"深圳 龙岗",
						sharenum:20,
						commentnum:30,
						goodnum:20
					},
					// 分享
					{
						userpic:"../../static/demo/userpic/12.jpg",
						username:"哈哈",
						sex:0, //0 男 1 女
						age:25,
						isguanzhu:false,
						title:"我是标题",
						titlepic:"",
						video:false,
						share:{
							title:"我是分享的标题",
							titlepic:"../../static/demo/datapic/14.jpg"
						},
						path:"深圳 龙岗",
						sharenum:20,
						commentnum:30,
						goodnum:20
					},
				]
			};
		},
		methods: {
			//点击切换
			changeTab(index) {
				this.tabIndex = index;
			},
			//打开发布页
			oppenAdd() {
				uni.navigateTo({
					url: '../add-input/add-input',
				})
			}

		}
	}
</script>

<style>
	
	.nav-left>view,
	.nav-right>view {
		font-size: 40upx;
	}
	.nav-left>view {
		color: #FF9619;
	}
	.nav-left {
		margin-left: 16upx;
	}
	.nav-right>view {
		margin-left: 40upx;
	}
	.nav-tab-bar {
		/* margin-left: -15upx; */
	}
	.nav-tab-bar {
		/* width: 100% !important; */
		/* margin-left: -20upx; */
		position: relative;
	}
	.nav-tab-bar>view {
		font-size: 32upx;
		padding: 0 15upx;
		font-weight: bold;
		color: #969696;
	}
	.active {
		color: #333333 !important;
	}
	.nav-tab-bar-line {
		/* border-bottom: 5upx solid #FEDE33; */
		background: #FEDE33;
		height: 6upx;
		/* border-top: 5upx solid #FEDE33; */
		width: 70upx;
		border-radius: 20upx;
		position: absolute;
		bottom: -2upx;
	}
	
	
</style>
