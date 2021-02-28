<template>
	<view>
		<swiper-tab-head 
		:tabBars="tabBars" 
		:tabIndex="tabIndex" 
		@tabtap="tabtap">
		</swiper-tab-head>
		
		<view class="uni-tab-bar">
			<swiper class="swiper-box" 
			:style="{height:swiperheight + 'px'}" 
			:current="tabIndex"
			@change="tabChange">
				<swiper-item v-for="(items,index) in newsList" :key="index">
					<scroll-view scroll-y class="list" @scrolltolower="loadmore(index)">
						<template v-if="items.list.length >0">
							<!-- 图文列表 -->
							<block v-for="(item,index1) in items.list" :key="index1">
								<index-list :item="item" :index="index1"></index-list>
							</block>
							<!-- 图文列表 -->
							<!-- 下拉加载更多 -->
							<load-more :loadtext="items.loadtext"></load-more>
							<!-- 下拉加载更多 -->
						</template>
						<template v-else>
							<!-- 无内容默认 -->
							<no-thing></no-thing>
						</template>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
		
	</view>
</template>

<script>
	import indexList from "../../components/index-list.vue";
	import swiperTabHead from "../../components/swiper-tab-head.vue";
	import loadMore from "../../components/common/load-more.vue";
	import noThing from "../../components/common/no-thing.vue";
	export default {
		components: {
			indexList,
			swiperTabHead,
			loadMore,
			noThing
		},
		data() {
			return {
				swiperheight:500,
				tabIndex: 0,
				tabBars: [{
						name: "关注",
						id: "guanzhu"
					},
					{
						name: "推荐",
						id: "tuijian"
					},
					{
						name: "体育",
						id: "tiyu"
					},
					{
						name: "热点",
						id: "redian"
					},
					{
						name: "财经",
						id: "caijing"
					},
					{
						name: "娱乐",
						id: "yule"
					},
				],
				newsList:[
					{
						loadtext:"下拉加载更多",
						list: [
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "小不点",
								isguanzhu: false,
								title: "如何用手账改变你的一生？",
								type: "img", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/27.jpg",
								infonum: {
									index: 0, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "洋葱头",
								isguanzhu: true,
								title: "走出去，才发现你跟别人差的不是一点半点",
								type: "video", //img:图片，video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								commentnum: 10,
								sharenum: 10,
								infonum: {
									index: 1, //0：没有操作，1顶，2踩
									dingnum: 11,
									cainum: 11,
								}
							}
						]
					},
					{
						loadtext:"下拉加载更多",
						list: [
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "洋葱头",
								isguanzhu: true,
								title: "走出去，才发现你跟别人差的不是一点半点",
								type: "video", //img:图片，video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								commentnum: 10,
								sharenum: 10,
								infonum: {
									index: 1, //0：没有操作，1顶，2踩
									dingnum: 11,
									cainum: 11,
								}
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "小不点",
								isguanzhu: false,
								title: "如何用手账改变你的一生？",
								type: "img", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/27.jpg",
								infonum: {
									index: 0, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "洋葱头",
								isguanzhu: true,
								title: "走出去，才发现你跟别人差的不是一点半点",
								type: "video", //img:图片，video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								commentnum: 10,
								sharenum: 10,
								infonum: {
									index: 1, //0：没有操作，1顶，2踩
									dingnum: 11,
									cainum: 11,
								}
							}
						]
					},
					{
						loadtext:"下拉加载更多",
						list: [
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "小不点",
								isguanzhu: false,
								title: "如何用手账改变你的一生？",
								type: "img", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/27.jpg",
								infonum: {
									index: 0, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "洋葱头",
								isguanzhu: true,
								title: "走出去，才发现你跟别人差的不是一点半点",
								type: "video", //img:图片，video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								commentnum: 10,
								sharenum: 10,
								infonum: {
									index: 1, //0：没有操作，1顶，2踩
									dingnum: 11,
									cainum: 11,
								}
							}
						]
					},
					{
						loadtext:"下拉加载更多",
						list: [
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "洋葱头",
								isguanzhu: true,
								title: "走出去，才发现你跟别人差的不是一点半点",
								type: "video", //img:图片，video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								commentnum: 10,
								sharenum: 10,
								infonum: {
									index: 1, //0：没有操作，1顶，2踩
									dingnum: 11,
									cainum: 11,
								}
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "小不点",
								isguanzhu: false,
								title: "如何用手账改变你的一生？",
								type: "img", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/27.jpg",
								infonum: {
									index: 0, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "洋葱头",
								isguanzhu: true,
								title: "走出去，才发现你跟别人差的不是一点半点",
								type: "video", //img:图片，video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								commentnum: 10,
								sharenum: 10,
								infonum: {
									index: 1, //0：没有操作，1顶，2踩
									dingnum: 11,
									cainum: 11,
								}
							}
						]
					},
					{
						loadtext:"下拉加载更多",
						list: [
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "小不点",
								isguanzhu: false,
								title: "如何用手账改变你的一生？",
								type: "img", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/27.jpg",
								infonum: {
									index: 0, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "洋葱头",
								isguanzhu: true,
								title: "走出去，才发现你跟别人差的不是一点半点",
								type: "video", //img:图片，video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								commentnum: 10,
								sharenum: 10,
								infonum: {
									index: 1, //0：没有操作，1顶，2踩
									dingnum: 11,
									cainum: 11,
								}
							}
						]
					},
					{
						loadtext:"下拉加载更多",
						list: [
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "洋葱头",
								isguanzhu: true,
								title: "走出去，才发现你跟别人差的不是一点半点",
								type: "video", //img:图片，video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								commentnum: 10,
								sharenum: 10,
								infonum: {
									index: 1, //0：没有操作，1顶，2踩
									dingnum: 11,
									cainum: 11,
								}
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "小不点",
								isguanzhu: false,
								title: "如何用手账改变你的一生？",
								type: "img", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/27.jpg",
								infonum: {
									index: 0, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "洋葱头",
								isguanzhu: true,
								title: "走出去，才发现你跟别人差的不是一点半点",
								type: "video", //img:图片，video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								commentnum: 10,
								sharenum: 10,
								infonum: {
									index: 1, //0：没有操作，1顶，2踩
									dingnum: 11,
									cainum: 11,
								}
							}
						]
					},
				]
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					let height = res.windowHeight-uni.upx2px(100)
					this.swiperheight = height;
				}
			});
		},
		//监听搜索框点击事件
		onNavigationBarSearchInputClicked(){
			uni.navigateTo({
				url:'../search/search',
			});
			
		},
		//监听原生标题栏按钮点击事件
		onNavigationBarButtonTap(e) {
			// console.log(JSON.stringify(e))
			switch (e.index){
				case 1:
				//打开发布页面
				uni.navigateTo({
					url:'../add-input/add-input',
				})
					break;
			}
			
		},
		methods: {
			// 下拉加载更多
			loadmore(index){
				if(this.newsList[index].loadtext !="下拉加载更多"){
					return;
				}
				this.newsList[index].loadtext="加载中...";
				setTimeout(()=>{
					let obj ={
						userpic: "../../static/demo/userpic/12.jpg",
							username: "小不点",
							isguanzhu: false,
							title: "如何用手账改变你的一生？",
							type: "img", // img:图文,video:视频
							titlepic: "../../static/demo/datapic/27.jpg",
							infonum: {
								index: 0, //0:没有操作，1:顶,2:踩；
								dingnum: 11,
								cainum: 11,
							},
							commentnum: 10,
							sharenum: 10,
						};
						
						this.newsList[index].list.push(obj);
						this.newsList[index].loadtext="下拉加载更多"
				},1000)
				
				
			},
			// tabbar点击事件
			tabtap(index) {
				this.tabIndex = index;
			},
			//滑动事件
			tabChange(e){
				//console.log(JSON.stringify(e.detail))
				this.tabIndex = e.detail.current;
			}
		},
	}
</script>
<style>
	.load-more{
		padding: 10upx;
		color: #aaa;
		text-align: center;
	}
</style>