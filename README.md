# 前端一些知识点积累
1、如何判断是否为数组：
```javascript
function isArrayFn(obj){
    if(typeof Array.isArray === 'function'){ //ES5方法
        return Array.isArray(obj);
    }else{
        return Object.prototype.toString.call(obj) === '[object Array]';
    }
}
```
