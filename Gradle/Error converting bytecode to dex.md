### 错误描述：
```
Error:Error converting bytecode to dex:
Cause: com.android.dex.DexException: Multiple dex files define Landroid/support/v7/widget/AdapterHelper$Callback;
Error:Execution failed for task ':app:transformClassesWithDexForDebug'.
> com.android.build.api.transform.TransformException: com.android.ide.common.process.ProcessException: java.util.concurrent.ExecutionException: java.lang.UnsupportedOperationException
```

根据提示信息可以知道是有重复的架包资源应用。检查项目libs文件夹以及app 的 build.gradle是否引用了不同的RecycleView.jar。我选择删除了libs目录下的RecycleView.jar
，然后重新编译工程即可。

```
compile 'com.android.support:recyclerview-v7:24.2.1'
```

### 总结：
遇到 Multiple .... 相关的编译错误，通常可以检查项目中时候存在重复的资源引用。保证唯一性即可。
