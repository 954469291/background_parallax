<template>
	<div class="home">
		<p v-for="item in 20" :key="item">aaaaaaaaaaaaaaaaaaaa</p>
		<div class="bgTest" id="bgTest" :style="{'background-position-y':positionY1+'px'}"></div>
		<p v-for="item in 20" :key="item+20">aaaaaaaaaaaaaaaaaaaa</p>
	</div>
</template>

<script>
	export default {
		name: "Home",
		data() {
			return {
				positionY1: 0, //背景Y轴偏移量
				Y1: 0,
				ratio: 0.5 //视差偏移率
			}
		},
		/**
		 * 
		 * */
		mounted() {
			window.addEventListener("scroll", this.handleScroll); //创建滚动监听，页面滚动回调handleScroll方法
				let bgTest = document.getElementById("bgTest");
				this.Y1 = bgTest.offsetTop * this.ratio

		},
		methods: {
			/**
			 * 背景视差偏移计算
			 * */
			handleScroll: function() {
				let scrollTop =
					window.pageYOffset ||
					document.documentElement.scrollTop ||
					document.body.scrollTop;
				this.positionY1 = this.Y1 - scrollTop * this.ratio; //原始高度-滚动距离*视差系数
				
			}
		},
		components: {}
	};
</script>
<style>
	.bgTest {
		height: 500px;
		background: url(../assets/bg.jpg) no-repeat;
		background-attachment: fixed;
		background-size: 100% 100%;
		font-size: 20px;

	}
</style>
