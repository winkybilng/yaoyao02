# yaoyao02
<!DOCTYPE html>
<html>
<head>
	<title>yaoyao02</title>
	<style type="text/css">
		.form1{
			margin: 20px 10px;
		}
		.form{
			margin: 25px 10px;
		}
		.name{
			font-weight: bold;
			margin: 15px;
		}
		.kuang{
			border: 1px solid #778899;
			outline: none;
			border-radius: 5px;
			-moz-border-radius:5px;
			height: 25px;
			width: 300px;
		}
		.submit{
			margin: 10px;
			height: 28px;
			width: 50px;
			background-color: #436EEE;
			color: white;
			font-weight: bold;
			border-radius: 5px;
			-moz-border-radius:5px;
			outline: none;
		}
		.check{
			margin-left: 70px;
			display: none;
			font-size: 80%;
			color: #778899;
		}
		.active .check{
			display: block;
		}
		.success .kuang{
			border: 1px solid green;
		}
		.success .check{
			color:green;
			display: block;
		}
		.erro .kuang{
			border: 1px solid red;
		}
		.erro .check{
			color: red;
			display: block;
		}
	</style>
</head>
<body>
	<form class="form" id="form">
		<div class="form1">
			<b class="name">名称</b>
			<input type="text" class="kuang" id="name0" onfocus="myFunction(this)" onblur="spring(this)">
		<p class="check" id="check0">
			必填，长度为4到16个字符
		</p>
		</div>
		<div class="form1">
			<b class="name">密码</b>
			<input type="password" class="kuang" id="name1" onfocus="myFunction(this)" onblur="spring(this)">
		<p class="check" id="check1">
			必填，长度为4到16个字符
		</p>
		</div>
		<div class="form1">
			<b class="name">密码确认</b>
			<input type="password" class="kuang" id="name2" onfocus="myFunction(this)" onblur="spring(this)">
		<p class="check" id="check2">
			请再次输入密码
		</p>
		</div>
		<div class="form1">
			<b class="name">邮箱</b>
			<input type="text" class="kuang" id="name3" onfocus="myFunction(this)" onblur="spring(this)">
		<p class="check" id="check3">
			必填
		</p>
		</div>
		<div class="form1">
			<b class="name">手机</b>
			<input type="text" class="kuang" id="name4" onfocus="myFunction(this)" onblur="spring(this)">
		<p class="check" id="check4">
			必填
		</p>
		</div>
		<button type="button" class="submit" id="submit">验证</button>
	</form>
	<script type="text/javascript">
		var password;
		var arr=new Array(5);
		function myFunction(x){
				x.parentElement.className="active";
				switch(x.id){
					case "name0":document.getElementById("check0").innerHTML = "必填，长度为4到16个字符";
					arr[0]=0;
					break;
					case "name1":document.getElementById("check1").innerHTML = "必填，长度为4到16个字符";
					arr[1]=0;
					break;					
					case "name2":document.getElementById("check2").innerHTML = "请再次输入密码";
					arr[2]=0;
					break;
					case "name3":document.getElementById("check3").innerHTML = "必填";
					arr[3]=0;
					break;
					case "name4":document.getElementById("check4").innerHTML = "必填";
					arr[4]=0;
				}
		}
		function spring(x){
			switch(x.id){
				case "name0":
				var reg= /^[\u4E00-\u9FA5A-Za-z0-9 ]+$/;
				if (reg.test(x.value)&&x.value.length>3&&x.value.length<17) {
				x.parentElement.className="success";
				document.getElementById("check0").innerHTML = "名称格式正确";
				arr[0]=2;
				} 
				else if (x.value==0) {
				x.parentElement.className="erro";
				document.getElementById("check0").innerHTML = "姓名不可以为空";
				}
				else {
				x.parentElement.className="erro";
				document.getElementById("check0").innerHTML = "姓名格式错误";
				}break;
				case "name1":
				var reg= /^[\u4E00-\u9FA5A-Za-z0-9 ]+$/;
				if (reg.test(x.value)&&x.value.length>3&&x.value.length<17) {
				x.parentElement.className="success";
				document.getElementById("check1").innerHTML = "密码格式正确";
				arr[1]=2;
				} 
				else if (x.value==0) {
				x.parentElement.className="erro";
				document.getElementById("check1").innerHTML = "密码不可以为空";
				}
				else {
				x.parentElement.className="erro";
				document.getElementById("check1").innerHTML = "密码格式错误";
				}
				password = x.value;
				break;
				case "name2":
				if (x.value==0) {

				}
				else if (x.value==password) {
					x.parentElement.className="success";
					document.getElementById("check2").innerHTML = "密码输入一致";
					arr[2]=2;
				} 
				else {
					x.parentElement.className="erro";
					document.getElementById("check2").innerHTML = "密码输入错误";
				}
				break;
				case "name3":
				x.parentElement.className="success";
				document.getElementById("check3").innerHTML = "邮箱格式正确";
				arr[3]=2;
				break;
				case "name4":
				x.parentElement.className="success";
				document.getElementById("check4").innerHTML = "手机格式正确";
				arr[4]=2;
			}
		}
		document.getElementById("submit").onclick=function(){
		var result = arr.every(function(item){
			return (item==2);
		});
		if (result) {
			alert("提交成功");
		} else {
			alert("输入有误");
		}
};
	</script>
</body>
</html>
