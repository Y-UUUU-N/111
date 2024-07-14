{% extends 'base.html' %}

{% block content %}
<h3>看视频赢奖励</h3>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>短视频</title>
    <style>
    .box-out {
        position: relative;
        #border: solid 1px #555;
        float: left;
        padding:0px 10px;
    }
    .box-in {
        position: absolute;
        left:0;
        top: 0рх;
        right: 0;
        bottom: 0;
        margin: auto;
    }
    .title-in {
        position: absolute;
        top: 240pх;
        left: 0;
        right: 0;
        margin: auto;
        text-align: center;
        height: 50px;
        line-height: 650px;
        font-size: 20px;
    }
    </style>
</head>
<body>
<div id="container">
{% for movie in movies %}
    <div class="box-out" style="height: 300px;width: 550px">
        <video class="movie box-in" data-file="{{ movie['file'] }}" width="450" height="250" controls>
            <source src="static/movies/{{movie['file']}}" type="video/mp4" />
        </video>
        <p class="title-in">{{movie['title']}}</p>
    </div>
{% endfor %}
</div>
<script>
    function resetContentPos(){
        var div = document.getElementById("container");
        var allWidth = document.body.clientWidth;
        var n = parseInt(allWidth / 20);
        var contentWidth = n * 20;
        div.style.marginLeft = (allWidth-contentWidth/1.12+"px")
    }
    (function (){
        resetContentPos();
    })();
    window.onresize = function(){
        resetContentPos();
    }
</script>
</body>
</html>

{% endblock %}
