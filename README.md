# 前端一些知识点积累
### 目录
1. [判断是否为数组](#1、判断是否为数组)
2. [user-select](#2user-select)
3. [-webkit-tap-highlight-color](#3-webkit-tap-highlight-color)
4. [-webkit-touch-callout](#4-webkit-touch-callout)
5. [input type='date'移动端无法触发change](#5input-typedate移动端无法触发change)
6. [移动端audio无法自动播放](#6移动端audio无法自动播放)
7. [MP4格式的播放时黑屏](#7MP4格式的播放时黑屏)

### 1、判断是否为数组
```javascript
function isArrayFn(obj){
    if(typeof Array.isArray === 'function'){ //ES5方法
        return Array.isArray(obj);
    }else{
        return Object.prototype.toString.call(obj) === '[object Array]';
    }
}
```
### 2、user-select

控制用户无法选择（现代浏览器）
```css
-webkit-user-select: none;
-moz-user-select: none;
-ms-user-select: none;
user-select: none;
```
### 3、-webkit-tap-highlight-color

设置a点击的时候高亮：
```css
a{
    -webkit-tap-highlight-color:rgba(0,0,0,.5);
}
```
### 4、-webkit-touch-callout

是否禁用系统默认处理的功能，例如：链接元素比如新窗口打开，img元素比如保存图像等等
```
-webkit-touch-callout: 属性
none： 系统默认菜单被禁用
inherit：系统默认菜单不被禁用
```
### 5、input type='date'移动端无法触发change
Android移动端input type='date' 并不能触发`change`和`input`监听事件，但是可以监听`blur`事件来代替，只不过不是在选择完毕后立即触发回调，而是在input失去焦点后触发回调。

### 6、移动端audio无法自动播放
这个是移动端系统的限制问题，解决的方案为：用户第一次触摸屏幕的时候立即播放并且立即暂停audio，右面就可以随便播放了。
```javascript
document.addEventListener('touchstart', function () {
    document.getElementsByTagName('audio')[0].play();
    document.getElementsByTagName('audio')[0].pause();
});
```
### 7、MP4格式的播放时黑屏
html5 video不能播放，能播放声音不能播放视频，黑屏：
浏览器播放视频的支持有限，MP4格式的视频只支持h.264的视频；
视频编码： AVC1 - 内置 FFmpeg 解码器(h264) 可以播放；
视频编码： mp4v - 内置 FFmpeg 解码器(mpeg4) 不可以播放；
声音压制的方式： AAC
如果出现上述问题，可以使用格式工厂转化下格式。
