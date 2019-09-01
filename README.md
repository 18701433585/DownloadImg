# DownloadImg
这是使用html2canvs的一个小工具 可以生成图片下载图片
直接上代码！！！
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no" />
		<title>tianmao</title>
		<!-- html2canvas就是这样一款前端插件,它的原理是将Dom节点在Canvas里边画出来 -->
		<script src="js/html2canvas.js"></script>
		<!-- 将canvas图片保存成图片 -->
		<script src="js/canvas2image.js"></script>
		<script src="js/base64.js"></script>
		<script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
		<style>
    * {
        margin: 0;
        padding: 0;
    }
	.backgrimg{
		width: 200px;
		height: 200px;
		display: none;
	}
	div img{
		width: 100%;
		height: 100%;
	}
</style>
	</head>
<body>
		<div class="test backgrimg">
			<img src="./img/2.jpg" alt="">
		</div>
		<div class="Img"></div> <!-- 放图片的地方 -->
		<div>
			<span class="Btnyu">预览</span>
			<span class="toCanvas">生成</span>
			<span class="toPic">下载<span>
		</div>	
</body>
<script>
	var test = $(".test").get(0); //将jQuery对象转换为dom对象
	$('.Btnyu').click(function(){
		$('.backgrimg').show();
	})
    // 点击转成canvas
    $('.toCanvas').click(function(e) {
        // 调用html2canvas插件
        html2canvas(test).then(function(canvas) {
			$('.Img').after(canvas);//把生成的canvas放在img
			$('.toPic').click(function(e) {
                var img = Canvas2Image.convertToImage(canvas);
				Canvas2Image.saveAsImage(canvas);
            });
		});
	});	
</script>
</html>
