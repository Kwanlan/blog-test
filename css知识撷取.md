# 浏览器渲染原理
1. 根据HTML构建HTML树（DOM)
2. 根据CSS构建CSS树（CSSOM）
3. 将两棵树合并成一棵渲染树（render tree）
4. layout布局（文档流，盒模型，计算大小和位置）
5. Paint绘制（把边框颜色，文字颜色，阴影等画出来）
6. compose合成（根据层叠关系展示画面）
## 如何用更新样式：
### 更新样式步骤：
JS/CSS>样式style>布局Layout>绘制Paint>合成composite
### 更新样式的代码例子：
• div.style.background:'pink'
• div.classList.add('red') 
• div.remove()  //直接删掉节点
## 三种代码更新方式的不同：
1. 过程全走一遍，使用了其他元素relayout。
2. 跳过layout，直接repaint+composite。
3. 跳过layout和Paint，改变transform，只需composite。

# tranform
作用：允许你=旋转，缩放，倾斜或平移给定元素
经验：一般要配合transition。inline元素不支持transform，需要变成block。
四个常用的功能：
1. translate位移
transform: translate(120px, 50%);
2. scale缩放
transform: scale(2, 0.5);
3. rotate旋转
transform: rotate(0.5turn);
4. skew倾斜
transform: skew(30deg, 20deg);

# CSS 动画的两种做法
## transition
过渡，补充中间帧
语法：transition：属性名 时长 过渡时间 延迟
## animation
声明关键帧添加动画
### 方法一：
```css
@keyframes slidein{
from{
            transform:translateX（0%）;
}
to{
transform:translateX（100%）;
}
```
### 方法二：
```css
@feyframes identifier{
0%{ top: 0; left:0;}
30%{top : 50%;}
100%{top:100px;}
}
```
# 感想：
css若没有有趣的素材做支撑，还是相当枯燥。赶快学完进入下一章。