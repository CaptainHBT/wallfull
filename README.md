# wallfull
<!DOCTYPE html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>瀑布流</title>
<style>
	*{
		margin:0;
		padding:0;
	}
	#container{
		position:relative;
	}
	.box{
		padding:5px;
		float:left;
		background-color:red;
		width:18%;
	}
</style>
</head>

<body>
	<div id="container">
    	<div class="box">
            1
            <br>
            <br>
        </div>
        <div class="box">
            2
            <br>
            <br>
            <br>
            <br>
            <br>
            <br>
        </div>
        <div class="box">
            3
            <br>
            <br>
            <br>
        </div>
        <div class="box">
            4
            <br>
            <br>
            <br>
            <br>
            <br>
            <br>
        </div>
        <div class="box">
            5
            <br>
            <br>
            <br>
            <br>
            <br>
            <br>
            <br>
            <br>
            <br>
        </div>
        <div class="box">
            6
            <br>
            <br>
            <br>
            <br>
            <br>
            <br>
        </div>
        <div class="box">
            7
            <br>
            <br>
            <br>
            <br>
            <br>
            <br>
            <br>
            <br>
            <br>
            <br>
        </div>
        <div class="box">
            8
            <br>
            <br>
            <br>
            <br>
            <br>
            <br>
        </div>
        <div class="box">
            9
            <br>
            <br>
            <br>
            <br>
            <br>
            <br>
        </div>
        <div class="box">
            10
            <br>
            <br>
            
            <br>
        </div>
        <div class="box">
            11
            <br>
            <br>
            <br>
            <br>
            <br>
            <br>
        </div>
        <div class="box">
            12
            <br>
            <br>
            <br><br>
            <br>
            <br>
            <br>
            <br>
            <br>
        </div>
        <div class="box">
            13
            <br>
            <br>
            <br>
            <br>
            <br>
            <br>
        </div>
    </div>
</body>
<script>
	window.onload=function(){
		imgLocation('container','box')
	}
	function imgLocation(parent,content){
		var cParent= document.getElementById(parent);
		var cContent=getChildElement(cParent,content);
		
		var boxHeightArr=[];
		for(var i=0;i<cContent.length;i++){
			if(i<5){
				boxHeightArr[i]=cContent[i].offsetHeight;
			}else{
				var minHeight=Math.min.apply(null,boxHeightArr);
				var minIndex = getMixHeightLocation(boxHeightArr,minHeight);
				cContent[i].style.position='absolute';
				cContent[i].style.top=minHeight+'px';
				cContent[i].style.left=cContent[minIndex].offsetLeft+'px';
				boxHeightArr[minIndex]+=cContent[i].offsetHeight
			}
			
		}
		
	}
	function getMixHeightLocation(boxHeightArr,minHeight){
		for(var i in boxHeightArr){
			if(boxHeightArr[i]==minHeight){
				return i
			}
		}	
	}
	function getChildElement(parent,content){
		var contentArr=[];
		var allContent=parent.getElementsByTagName('*');
		for(var i=0;i<allContent.length;i++){
			if(allContent[i].className==content){
				contentArr.push(allContent[i]);
			}
		}
		return 	contentArr;
	}
</script>
</html>
