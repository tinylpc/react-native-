# react-native-问题汇总(0.39)

1、 按照官方文档自定义模块,运行时报找不到这个模块，最终发现在Application中注册模块是没效果的，需要在MainActivity中注册
```
 mReactInstanceManager = ReactInstanceManager.builder()
                .setApplication(getApplication())
                .setBundleAssetName("index.android.bundle")
                .setJSMainModuleName("index.android")
                .addPackage(new MainReactPackage())
                //需要在这个地方注册才行
                .addPackage(new MyToastPackage())
                .setUseDeveloperSupport(BuildConfig.DEBUG)
                .setInitialLifecycleState(LifecycleState.RESUMED)
                .build();
```

2、React Native加载本地图片(Android)

    1.将图片放到android/app/src/main/res/drawable-xxx目录下
  
    2.重新编译安装
  
    3.js文件中引用<Image source={require('image!launchscreen')}></Image>,launchscreen即为文件名
    
3、https://github.com/race604/react-native-viewpager改变pager高度方式

   在ViewPager标签外层再包裹一层View标签即可
   ```
   <View style={styles.pager}>
         <ViewPager style={styles.pager}
                    dataSource={this.state.dataSource}
                    renderPage={this._renderPage}
                    isLoop={true}
                    autoPlay={true}/>
   </View>
   ```
  
