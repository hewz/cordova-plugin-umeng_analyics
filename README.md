# cordova-plugin-umeng_analyics

友盟官网的Cordova插件比较乱，文档有错误，引用的库也是过时的。还有Android和iOS竟然各自独立。

基于17年10月最新lib整理了一下，测试可用。
  
* Android lib version: 6.1.2
* iOS lib version: 4.2.5(NO IDFA)

## 使用说明
### 1.安装插件
cordova plugins add https://github.com/hewz/cordova-plugin-umeng_analyics.git

### 2.调用

初始化：

```
MobclickAgent.init('your key', 'your channel');
```

自定义事件：

```
MobclickAgent.onEvent('event_id');
```

其它问题请参考官方文档。