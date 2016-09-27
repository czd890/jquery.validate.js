# jquery.validate.js
## 修改官方代码 version：1.15.1，支持非form标签包，容器增加必须的class：validateContainer。
例如：

```html
    <div id="x" class="validateContainer">
        <input data-rule-required="true" data-rule-number="true" data-rule-digits="true" acc="x" Acc2="xx" AcAc="3" acAc="4" name="xx" />
        <input type="submit" value="submit" />
    </div>
    <script src="jquery-3.1.0.js"></script>
    <script src="jquery.validate.js"></script>
    <script>
        $("#x").validate();
    </script>
```
在官方代码上增加方法：
```js
getContainer: function (element) {
            var container = $(element).closest('.validateContainer')[0];
            container = container || element.form;
            return container;
        }
```
 以及替换element.form调用方式为 $.validator.getContainer(element)
