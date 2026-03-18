## 基于xml的脚本
jar包太大无法上传git

jar 包下载地址：

通过网盘分享的文件：rap-template-1.0-SNAPSHOT-with-deps.jar
链接: https://pan.baidu.com/s/1OsDP6eX0GFUt5bD39rOsIQ?pwd=j1ba 提取码: j1ba 
--来自百度网盘超级会员v8的分享

使用方法
```shell
java -jar rpa-template.jar main.xml
```

以下是xml实例
demo1:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<rpa id="helloword" type="101">
    <var name="index" value="1"/>
    <while expr="#index&lt;10">
        <echo msg="'hello'+#index"/>
        <putvar name="index" value="#index+1"/>
    </while>
</rpa>
```
demo2:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<rpa id="36kr_article_detail" type="101">
    <!-- 初始化浏览器 -->
    <chrome>
        <!-- 定义一个变量pageno，初始值为1 -->
        <var name="pageno" value="1"/>
        <!-- 打开36氪的融资快讯页面 -->
        <chrome_page url="'https://pitchhub.36kr.com/financing-flash'" >
            <!-- 循环50次 -->
            <while expr="#pageno&lt;50">
                <!-- 等待3秒 -->
                <sleep seconds="3"/>
                <!-- 将pageno的值加1 -->
                <putvar name="pageno" value="#pageno+1"/>
                <!-- 如果pageno的值小于3 -->
                <if expr="#pageno&lt;3">
                    <!-- 滚动页面 value 为高度，小于0 则滚动到页面底部-->
                    <page_scroll value="-1"/>
                </if>
                <!-- 如果pageno的值大于2 -->
                <if expr="#pageno&gt;2">
                    <!-- 点击融资快讯页面中的加载更多按钮 -->
                    <page_click selector=".kr-loading-more-button.show"/>
                </if>
                <!-- 等待3秒 -->
                <sleep seconds="3"/>
                <!-- 滚动页面 -->
                <page_scroll value="-1"/>
            </while>
        </chrome_page>
    </chrome>
</rpa>
```
