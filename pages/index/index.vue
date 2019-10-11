<template>
	<view>
		<view class="canvasView">
			<canvas style="width: 300px; height: 400px;" canvas-id="firstCanvas"></canvas>
		</view>
		<view class="button-sp-area" style="margin:20px;">
			<button type="default" plain="true" size="default">保存后分享</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				avatar: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1570789697919&di=45a5917f26638befb8a55ccaca1bf7d4&imgtype=jpg&src=http%3A%2F%2F5b0988e595225.cdn.sohucs.com%2Fimages%2F20180622%2Fde8a457b8ef34f5ab443aa2eb8c5e462.jpeg',
				avatars:'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1570796030852&di=c14c1de985029fa0e5d20e1998ab5802&imgtype=0&src=http%3A%2F%2F5b0988e595225.cdn.sohucs.com%2Fimages%2F20180629%2F434414ae0985447ebe3c6e49145eedc0.jpeg'
			}
		},
		onReady: function(e) {
			var context = uni.createCanvasContext('firstCanvas')

			
			//绘制文字
			context.setFontSize(16)
			context.fillText('你好', 10, 245)
			context.fillText('我是新橙科技的销售员', 10, 265)
			context.fillText('这是我的名片，还请惠存。', 10, 285)
			context.fillText('谢谢', 10, 305)

			
			//绘制头像
			context.beginPath(); //开始绘制
			context.save();
			//先画个圆，前两个参数确定了圆心 （x,y） 坐标  第三个参数是圆的半径  四参数是绘图方向  默认是false，即顺时针
			// r=52/2   52 / 2 + 124表示圆心位置的x  为了确定图片从中心开始绘制
			context.arc(52 / 2 + 124, 52 / 2 + 315, 52 / 2, 0, Math.PI * 2, false);
			context.clip(); //画好了圆 剪切  原始画布中剪切任意形状和尺寸。
			context.drawImage(this.avatar, 124, 315, 52, 52);
			context.restore()
			
			//绘制头像下的文字
			context.setFillStyle("#ccc")
			context.setFontSize(12)
			context.setTextAlign('center')
			context.fillText('长按识别二维码', 150, 385)
			
			
			//绘画矩形
			//开始坐标
			context.moveTo(10, 30);
			// 左上角
			context.arcTo(10, 10, 20, 10, 10);
			// 右上角
			context.arcTo(300, 10, 300, 20, 10);
			// 右下角
			context.arcTo(300, 200, 200, 200, 10);
			// 左下角
			context.arcTo(10, 200, 10, 190,10);
			context.closePath();
			context.clip()
			context.restore()
			context.stroke()
			context.save()
			
			//绘制矩形中的地址矩形
			context.beginPath()
			context.setFillStyle('#ececec')
			context.fillRect(10, 140, 290, 60)
			context.arc(300, 200, 200, 200, 10)
			context.arc(10, 200, 10, 190,10)
			context.closePath();
			context.save()
			
			//绘制地址
			context.setFillStyle("#888")
			context.setFontSize(12)
			context.fillText('北京市朝阳区', 70, 170)
			context.save()
			
			
			//绘制公司
			context.setFillStyle("#888")
			context.setFontSize(12)
			context.setTextAlign('right')
			context.fillText('新橙科技有限公司', 280, 35)
			
			
			//绘制头像
			context.beginPath(); //开始绘制
			context.save();
			//先画个圆，前两个参数确定了圆心 （x,y） 坐标  第三个参数是圆的半径  四参数是绘图方向  默认是false，即顺时针
			// r=52/2   52 / 2 + 124表示圆心位置的x  为了确定图片从中心开始绘制
			context.arc(52 / 2 + 40, 52 / 2 + 40, 52 / 2, 0, Math.PI * 2, false);
			context.clip(); //画好了圆 剪切  原始画布中剪切任意形状和尺寸。
			context.drawImage(this.avatars, 40, 40, 52, 52);
			context.restore()
			
			
			//绘制个人信息
			context.setFillStyle("#000")
			context.setFontSize(16)
			context.fillText('小橙子', 160, 55)
			context.save();
			
			context.setFillStyle("#888")
			context.setFontSize(12)
			context.setTextAlign('left')
			context.fillText('管理员', 110, 80)
			context.fillText('15234567898', 110, 100)
			context.fillText('xiaochengzi@icourt.cc', 110, 120)
			context.save();
			
			context.draw()
		},
		methods: {
			
		}
	}
</script>

<style>
	.canvasView {
		margin: 50rpx 10rpx 0;
		border: 1rpx solid #ccc;
	}
</style>
