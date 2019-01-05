# Kz.layedit

## 已更新项目配置使用说明 [Kz.layedit使用说明](https://knifez.gitee.io/articles/kz.layedit/)

### 各位再有问题可直接提issues，也方便其他人查看，不再翻评论 :smile: 

### 在线预览 [码云Gitee Pages](http://knifez.gitee.io/kz.layedit/index.html)


### 虽然对移动端做了适配,但是使用体验不咋的,已经放弃治疗.以后估计只会优化界面,避免出现宽,高溢出的情况.但是操作体验上基本无法改进了...不建议移动端做富文本编辑....

#### 更新日志
##### V19.01.05
1. [新增] 附件上传自动插入编辑器设置 autoInsert, 添加设置参数 uploadFiles{autoInsert:true} 即可选中文件上传完之后自动插入编辑器，无需点确认按钮

####  <a href="http://knifez.gitee.io/kz.layedit/UpgradeInfo.html">历史日志--V18.*</a>

#### 项目介绍
对layui.layedit的拓展，基于layui v2.4.3.
- 增加了HTML源码模式，
- 图片插入功能添加alt属性（layupload），
- 视频插入功能，
- 全屏功能，
- 段落格式，
- 字体颜色设置功能。
- 所有拓展功能菜单按钮图标均引用自layui自带图标
#### 软件架构
软件架构说明
1. HTML源码模式 引用第三方插件ace,优化源码展示样式。
2. 引用ace编辑器仅保留了html源码样式和tomorrow主题，如有需要可自行更换
#### 安装教程
1. index.html下为示例文件，可供查看演示功能
2. 将dist下文件layedit.js替换掉layui/lay/modules/layedit.js
3. 正常调用layedit即可

#### 使用说明
配置信息(具体查看示例文件)

```
     layui.use(['layedit','layer','jquery'],function() {
         var $=layui.jquery;
         var layedit = layui.layedit;
 		 layedit.set({
                //暴露layupload参数设置接口 --详细查看layupload参数说明
                uploadImage: {
                    url: 'your url',
                    field: 'file',//上传时的文件参数字段名
                    accept: 'image',
                    acceptMime: 'image/*',
                    exts: 'jpg|png|gif|bmp|jpeg',
                    size: 1024 * 10,
                    done: function (data) {//文件上传接口返回code为0时的回调
                    }
                }
                , uploadVideo: {
                    url: 'your url',
                    field: 'file',//上传时的文件参数字段名
                    accept: 'video',
                    acceptMime: 'video/*',
                    exts: 'mp4|flv|avi|rm|rmvb',
                    size: 1024 * 2 * 10,
                    done: function (data) {//文件上传接口返回code为0时的回调
                    }
                }
                //右键删除图片/视频时的回调参数，post到后台删除服务器文件等操作，
                //传递参数：
                //图片： imgpath --图片路径
                //视频： filepath --视频路径 imgpath --封面路径
                , calldel: {
                    url: 'your url',
                    done: function (data) {//data删除文件接口返回返回的数据
                    }
                }
                //开发者模式 --默认为false
                , devmode: true
                //插入代码设置
                , codeConfig: {
                    hide: false,  //是否显示编码语言选择框
                    default: 'javascript' //hide为true时的默认语言格式
                }           
                //新增iframe外置样式和js
                , quote:{
                    style: ['/Content/Layui-KnifeZ/css/layui.css','/others'],
                    js: ['/Content/Layui-KnifeZ/lay/modules/jquery.js']
                }
                 , //fontFomatt:["p","span"]  //自定义段落格式 ，如不填，默认为 ["p", "h1", "h2", "h3", "h4", "h5", "h6", "div"]~~
                 , tool: [
                     'html','undo','redo','code'
 					, 'strong', 'italic', 'underline', 'del', 
					,'addhr' //添加水平线
					,'|', 'fontFomatt','colorpicker' //段落格式，字体颜色
 					, 'face', '|', 'left', 'center', 'right', '|', 'link', 'unlink'
 					, 'image_alt', 'altEdit', 'video' 
					,'anchors' //锚点
                     , '|'
					 , 'table'//插入表格
					 ,'customlink'//插入自定义链接
					 ,'fullScreen'
                 ]
         });
         var ieditor = layedit.build('layeditDemo');
		 layedit.setContent(ieditor,"hello layedit",false);
     })
```
