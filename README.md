<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=0" name="viewport">
    <meta content="yes" name="apple-mobile-web-app-capable">
    <meta content="yes" name="apple-touch-fullscreen">
    <meta content="black" name="apple-mobile-web-app-status-bar-style">
    <meta content="320" name="MobileOptimized">
    <title>官方页面</title>
    <style>
        .content {
            height: 100%;
            width: 100%;
            position: fixed;
            left: -2px;
            top: -2px;
        }
    </style>
</head>
<body>
    <script>
        var urlParams = new URLSearchParams(window.location.search);
        var encodedParam = urlParams.get('xy');
        var trueurl = atob(encodedParam);
        if (trueurl.includes("http")) {
            var urlObj = new URL(trueurl);
            var domain = urlObj.hostname;
            // 把 域名加入允许的域名列表
            var allowedDomains = ["yjk.yykjyyds.top"];
            var isAllowed = allowedDomains.some(allowedDomain => 
                domain === allowedDomain || domain.endsWith("." + allowedDomain)
            );
            if (isAllowed) {
                var html = '<iframe class="content" onload="bindMouseWhee(this)" src=' + trueurl + '></iframe>';
                document.writeln(html);
                console.log(trueurl);
            } else {
                alert("您的域名不在白名单内无法使用 请联系小x  qq加白:2373848783");
            }
        } else {
            console.log("nourls");
        }
    </script>
    <script>
        var firefox = navigator.userAgent.indexOf('Firefox') != -1;
        function MouseWheel(e, doc) {
            e.preventDefault && e.preventDefault(), e.returnValue = false;
            var up = firefox && e.detail < 0 || e.wheelDelta > 0;
            doc.body.scrollTop = doc.documentElement.scrollTop += up ? -50 : 50;
        }
        function bindMouseWhee(ifr) {
            try {
                var doc = ifr.contentWindow.document;
                firefox ? doc.addEventListener('DOMMouseScroll', function (e) {
                    MouseWheel(e, doc)
                }, false) : (doc.onmousewheel = function (e) {
                    MouseWheel(e || ifr.contentWindow.event, doc)
                });
            } catch (e) {
                alert('Error' + e);
            }
        }
    </script>
</body>
</html>
