<template>
	<view >
			<view class="" style="height: 500rpx;">
				
			</view>
			<view  
			style="box-sizing: border-box;
			position: relative;
			 display: flex;
			 flex-direction: column;
			 padding: 100rpx 0;
			 border-radius: 40rpx;
			 margin: 25rpx; background: #928b8533; height: 400rpx; ">
			<view class="" style=" display: flex; justify-content: center; left: 50%;transform: translateX(-50%); position: absolute; top: -100rpx;" >
				<image style="z-index: 99; width: 200rpx; height: 200rpx; border: 1px solid #fff; border-radius: 50%;"
				src="../static/img/hn7.jpg" mode="" @click="head()"></image>
				</view>
			<uni-title color="#fff" title="冯梓铭"type="h1" align="center"></uni-title>
			<view class="" style="display: flex; justify-content: space-around;">
				<view class="" style="color: #fff; border: #fff solid 2rpx; border-radius: 30rpx; font-size: 30rpx; padding: 10rpx;">
					IP属地: 浙江
				</view>
				<view class="" style="color: #fff; border: #fff solid 2rpx; border-radius: 30rpx; font-size: 30rpx; padding: 10rpx;">
					00后 狮子座
				</view> 
				<view class="" style="color: #fff; border: #fff solid 2rpx; border-radius: 30rpx; font-size: 30rpx; padding: 10rpx;">
					爱好: 打羽毛球
				</view> 
			</view>
		</view>
		<view style="display: flex; justify-content: space-around; " >
			<view v-for="(item,index) in chioce" :key="index"
			:class="current == index?'act':''" 
			@click="toggle(index)"
			style="color: #fff;  font-size: 36rpx; ">
				{{item}}
			</view>
			
		</view>
		<view class="" v-if="current == 0">
			<qiun-data-charts :chartData="grade" type="column"></qiun-data-charts>
		</view>
		<view class="" v-if="current == 1">
			<view class="">
				<view v-for="(item,index) in list" :key="index">
					<view class=""style="display: flex;flex-direction: column;
					margin: 40rpx;
					padding: 35rpx;
					border-radius: 30rpx;
					 background: #fff;">
						<text style="color:#d6d6d6;">{{item.time}}</text>
						<uni-title :title="item.title" type="h4" color="#888888"></uni-title>
						<swiper v-if="item.img" circular 
						style=" width: 400rpx; height: 300rpx;">
							<swiper-item v-for="(item2,index2) in item.img" 
								:key="index2">
						<image style="border-radius: 30rpx; width: 100%; height: 100%;"
							@click="pre(item.img, index2)"	:src="item2" mode=""></image>
							</swiper-item>
						</swiper>
						<view class="" style="margin: 20rpx 0;">
							<!-- <uni-badge text="10" type=""> -->
				<uni-badge size="small" :text="item.st" absolute="rightBottom" type="warning">
							<uni-icons v-if="item.st == 0" type="fire" 
							@click="add(item.id)"></uni-icons>
							<uni-icons v-else type="fire-filled"
							@click="add(item.id)"></uni-icons>
							</uni-badge>
						</view>
					</view>
				</view>
				
				<!-- <image src="" mode=""></image> -->
				<uni-title align="center" title=" " type="h4" color="#888888"></uni-title>
			</view>
		</view>
		<view class="" v-if="current == 2">
			<view class="" style="display: flex; justify-content: center;margin: 20rpx 0;">
				<video style="border-radius: 30rpx; border: 2rpx solid #fff;" src="../static/video/hn.mp4" controls></video>
			</view>
			<uni-title align="center" title="ps:(转自航拍中国湖南)" type="h4" color="#888888"></uni-title>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				current:0,
				chioce:['本学期情况','动态','有空来湖南康康'],
				list:[
	{id:0,title:'6点钟的下沙',
	img:['../static/img/c08.jpg','../static/img/c09.jpg',
	'../static/img/c04.jpg'], 
	time:'2022-09-28 06:45',
	st:1
	},
	{id:1,title:'奖学金!',
	time:'2022-09-15 09:20',
	st:1
	},
	{id:2,title:'老校区"坐牢"',
	img:['../static/img/c12.jpg','../static/img/c13.jpg'],
	time:'2022-07-01 15:01',
	st:0
	},
	{id:3,title:'久违的满分!',
	img:['../static/img/math.jpg'],
	time:'2022-06-29 22:01',
	st:0
	},
	{id:4,title:'严重怀疑老师1000米放水...',
	img:['../static/img/run2.jpg'],
	time:'2022-06-07 11:06',
	st:0
	},
	{id:5,title:'8公里~',
	img:['../static/img/run1.jpg'],
	time:'2022-05-23 20:10',
	st:0
	},
	{id:6,title:'四史知识竞赛',
	img:['../static/img/ss1.jpeg', '../static/img/ss2.jpg', '../static/img/ss3.jpg'],
	time:'2022-05-08 18:00',
	st:0
	},
	{id:7,title:'学生社团每月之星!',
	time:'2022-03-20 18:00',
	st:0
	},
	{id:8,title:'结束也意味着开始',
	time:'2022-03-07 12:00',
	img:['../static/img/jx4.jpg', '../static/img/jx3.jpg', '../static/img/jx2.jpg','../static/img/jx1.jpg'],
	st:0
	}
				],
			grade:{
				categories:['WEB前端交互','MySQL','大学英语','PHP','高等数学','计算机网络'],
				series:[{name:'非选修课成绩',data:[90,86,99,90,96,94]}]
			}
			}
		},
		methods: {
			toggle(index){
				this.current = index
			},
			pre(urls, current){
				uni.previewImage({
					urls,
					current
				})
			},
			add(id){
				this.list[id].st ++
			},
			head(){
				let urls = ['../static/img/hn7.jpg']
				uni.previewImage({
					urls
				})
			}
		}
	}
</script>

<style>
page{
	background-image: linear-gradient(to right, #a8edea 0%, #fed6e3ee 100%);
}
.act{
	border-bottom: 6rpx solid #ccc;
}
</style>
