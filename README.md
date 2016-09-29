#cordova-plugin-umeng_analyics

友盟官网的Cordova插件比较乱，文档有错误，引用的库也是过时的。还有Android和iOS竟然各自独立。

基于8月最新lib整理了一下，测试可用。
  
* Android lib version: 6.0.1
* iOS lib version: 4.0.4

##使用说明
###1.安装插件
cordova plugins add https://github.com/hewz/cordova-plugin-umeng_analyics.git
###2.设置Umeng App Key
根据官方文档：

Android在plugin.xml中替换

iOS在第三步代码中写入

###3.插入代码
Android在主界面中加入并初始化：

```
/**
 * onCreate中调用
 */
private void initUmengSDK() {
    MobclickAgent.setScenarioType(this, EScenarioType.E_UM_NORMAL);
    MobclickAgent.setDebugMode(true);
    MobclickAgent.openActivityDurationTrack(false);
    // MobclickAgent.setSessionContinueMillis(1000);
}

@Override
protected void onResume() {
    super.onResume();
    MobclickAgent.onResume(this);
}

@Override
protected void onPause() {
    super.onPause();
    MobclickAgent.onPause(this);
}
```

iOS在AppDelegate.m中找到 (BOOL)application:(UIApplication*)application didFinishLaunchingWithOptions:(NSDictionary*)launchOptions 方法，添加下面的代码：

```
 UMConfigInstance.appKey = @"Your Appkey";  
 UMConfigInstance.channelId = @"Your ChannelId";"  
 UMConfigInstance.eSType=E_UM_GAME;//友盟游戏统计，如不设置默认为应用统计  
 [MobClick startWithConfigure:UMConfigInstance];
```

其它问题请参考官方文档。