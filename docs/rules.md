---
comments: true
tags:
  - 维基
  - 技术
icon: material/ruler-square-compass
---

# 规定

<html>
    <head>
        <!-- Load jQuery  -->
        <script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.0/jquery.min.js"></script>

        <!-- Load WysiBB JS and Theme -->
        <script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.0/jquery.min.js"></script>
        <script src="http://cdn.wysibb.com/js/jquery.wysibb.min.js"></script>
        <link rel="stylesheet" href="http://cdn.wysibb.com/css/default/wbbtheme.css" />
        <script src="/js/lang/cn.js"></script>
    
        <!-- Init WysiBB BBCode editor -->
        <script>
        $(document).ready(function() {
        var wbbOpt = {
            lang : 	 "cn",
            buttons: "bold,italic,underline,|,img,link,|,code,quote"
        }
        $("#editor").wysibb(wbbOpt);
        });
        </script>
    </head>
    <body>
        <textarea id="editor">在这里写入文本。</textarea>
    </body>
</html>