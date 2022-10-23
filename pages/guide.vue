<template>
	<view style="width: 100%; height: 100%;">
		<swiper @change="sub" style="width: 100%; height: 100%;" >
			<swiper-item v-for="(item,index) in imgList" :key="index">
				<image @click="sw()" style="width: 100%; height: 100%;" :src="item" mode=""></image>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				num : 0,
				imgList:[
					'../static/img/hn1.jpg',
					'../static/img/hn5.jpg',
					'../static/img/hn3.jpg',
					'../static/img/hn7.jpg',
				]
			}
		},
		methods: {
			sub(e){
				this.num = e.detail.current
				
			},
			sw(){
				if(this.num == this.imgList.length - 1){
					setTimeout(()=>{
						uni.navigateTo({
							url:'home'
						})
					},1500)
				}
			}
		}
	}
</script>

<style>
page{
	height: 100%;
}
</style>
