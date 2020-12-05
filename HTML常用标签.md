# a 标签 超链接
## 属性
* href      hyper reference     链接本体，通常是个网址
* target    指定在哪个窗口打开超链接
* download  下载而非查看网页
* rel=noopener  防止BUG（待学）
### a标签的href取值  <a href="可取的值">超链接</a>
1. 网址
* https://
* http://
* //        （无协议网址）
2. 路径
* 绝对路径
/a/b/c      a之前的/表示的是http服务开启的目录      带/表示绝对路径，故不要在资源管理器中双击打开html文件，这样做将会使其地址开头变为file:///xxxxxxx，点击网页中的超链接会出现定位错误。
* 相对路径
a/b/c       在html的当前目录下打开
* 直接写文件名
会在当前目录寻找
example.html 或 ./example.html 都是正确的写法
3. 伪协议
javascript:xxxxxxxx;        中间的x为代码
javascript:;        冒号紧接分号，为空的伪协议；点击不会发生任何事，某些特殊场景会用到
mailto:邮箱     <a href="mailto:xxxxxxxx@xx.com">发邮件给我</a>
telto:电话号    <a href="telto:1380371xxxx">打电话给我</a>
4. id
href=#xxx
### a标签的作用：跳转
* 外部页面
* 内部锚点
* 邮箱或电话
### a标签的target取值
* _blank    在空白页打开
* _self     在当前页打开；在层叠页面的本身打开；为默认值
* _top      在（层叠页面的）最顶层页面打开
* _parent   在当前链接iframe的上一层打开
<hr>

# table 标签 表格
## 相关的标签
* thead
* tbody
* tfoot
## ******************
* tr    [table row]
* th    [table head]
* td    [table data]
## 相关的样式
* table-layout
* border-collapse
<hr>

# img 标签 图片
作用：发出get请求，展示一张图片
## 属性
* alt   如果加载图片失败则显示其中内容
* height 高 ，只写高度的话宽度会自适应
* width 宽  ，只写宽度的话高度会自适应
* src 资源

同时规定宽和高有可能使图片变形。作为前端工程师应尽力避免发生。
## 事件 
* onload
* onerror

监听图片是否加载成功。如果成功调用onload，失败则调用onerror
可在script标签内使用
## 响应式
maxwidth:100%
应用于手机页面
<hr>

# form 标签 表单
作用：发get或post请求，然后刷新页面
## 属性
* acton 控制请求哪个页面
* method 控制使用get还是post方法
* autocomplete
* target
## 事件
* onsubmit
<hr>

# input 标签 输入
贼像 visualbasic 的控件

<hr>

# 打开html网页的专业方法
## 通过http-server来预览，步骤：
1. yarn global add http-server
2. http-server . -c-1       -c  缓存；  -c-1  不要缓存。    http-server可缩写为hs  
3. 通过网址访问网页，不要忘记在最后加上html的文件名
## 通过parcel来预览，步骤：
1. yarn global add parcel
2. parcel 空格 <html文件名> 回车
3. 直接打开给出的地址
<hr>

# chrome控制台调试步骤
1. 唤出 检查元素 控制台
2. 控制台置于下方
3. （可选）关掉手机模拟
4. 选项卡切换至 Network
5. 【重要】选中下方的 Preserve log
6. 操作或刷新页面