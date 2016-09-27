# jquery.validate.js
修改官方代码，支持非form标签包含

例如：
容器增加必须的class：validateContainer。
<html>
<head>
</head>
<body>
    <div id="x" class="validateContainer">
        <input data-rule-required="true" data-rule-number="true" data-rule-digits="true" acc="x" Acc2="xx" AcAc="3" acAc="4" name="xx" />
        <input type="submit" value="submit" />
    </div>
    <script src="jquery-3.1.0.js"></script>
    <script src="jquery.validate.js"></script>
    <script>
        $("#x").validate();
    </script>
</body>
</html>

在官方代码上增加方法：
getContainer: function (element) {
            var container = $(element).closest('.validateContainer')[0];
            container = container || element.form;
            return container;
        }
        
  替换element.form实现为 $.validator.getContainer(element)
