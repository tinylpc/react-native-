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
