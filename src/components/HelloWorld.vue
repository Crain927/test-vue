<style type="text/css">
	.hello img {
		margin: 20px auto;
	}
	
	#canvasImgDom {
		padding: 10px;
		width: 500px;
		margin: 20px auto;
		background-color: gray;
		color: #fff;
	}
	
	#canvasImgDom ul {
		width: 100%;
		text-align: left;
	}
</style>
<template>
	<div id="hello" class="hello">
		<div id="canvasImgDom">
			<h2>完成思路：</h2>
			<ul>
				<li>1、利用
					<a href="http://html2canvas.hertzen.com/getting-started/" target="_blank">html2canvas</a> 插件，把html用canvas画出来；</li>
				<li>2、new Image()创建图片，插入到DOM中。</li>
			</ul>
		</div>
		<p>下面的就是生成的Img：</p>
	</div>
</template>
<script>
	import html2canvas from 'html2canvas';
	export default {
		name: 'HelloWorld',
		created() {
			this.$nextTick(() => {
				console.log($(".hello"))
				html2canvas(document.getElementById("canvasImgDom")).then(function(canvas) {
					var image = new Image();
					image.src = canvas.toDataURL("image/png");
					//					$("#canvasImgDom").css('display',"none");
					document.getElementById("hello").appendChild(image)
				});
			})
		},
		data() {
			return {
				msg: 'Welcome to Your Vue.js App'
			}
		},
		methods: {

		}
	}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	h1,
	h2 {
		font-weight: normal;
	}
	
	ul {
		list-style-type: none;
		padding: 0;
	}
	
	li {
		display: inline-block;
		margin: 0 10px;
	}
	
	a {
		color: #42b983;
	}
</style>