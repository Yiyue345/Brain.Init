> Flutter made easy
> 这可不是我说的啊，他们的 readme 就是这么写的

虽然他们的文档已经写得很好了，但我还是想专门写点东西
# Getx 是个啥

这是一个很方便使用的包，让状态管理、依赖注入和路由管理都变得简单多了，而且拿它写 MVVM 体感上和安卓原生是差不多的

当然它最主要的用途还是管理状态（数据），毕竟你也不想拖着`InheritedWidget`写一大堆模板代码吧

> 当然管理状态还有像 [provider](https://pub.dev/packages/provider) 之类的包，可以都去了解一下，然后看看哪种更合适你（或者是你的项目）

# 状态管理

状态管理说着高级，实际上主要还是在不同的 Widget 之间共享变量

## 简单的基本用法

现在如果有两个页面 `PageA`和`PageB`，它们同时可以修改一个变量`count`并显示，那我们怎么才能让修改在两个页面间同步呢

聪明的你肯定想到在它们的父组件里面加个`InheritedWidget`，但是吧每次都要创建这么一个类加上一堆长长的方法名，也太麻烦了

此时 Getx 的 `controller`就派上用场了，顾名思义它是一个控制器，像`ViewModel`一样生命周期独立于视图（当然在合适的时机也会自动释放啦）。于是需要共享的变量就可以放在里面

```dart
class CountController extend GetxController {
    int count = 0;
}
```

然后在要使用这个变量之前初始化一下这个 `controller`（这部分涉及 Getx 的[依赖管理](#依赖管理)）

```dart
Get.put(CountController()); // 初始化一个 CountController，并将它加入 Getx 的依赖管理器中
```
然后在需要使用这个变量的时候获取这个`controller`的实例
```dart
class PageA extend StatelessWidget {
    @override
    Widget build(BuildContext context) {
    
        final controller = Get.find<CountController>(); // 在依赖管理器中找到一个 CountController 对象
        print(controller.count);
        
        ...
    }
}
```
就这么简单

但还有更方便的，因为我们要把这个`count`显示出来，所以在它变化时要更新 UI 就得用`setState`。可是如果我想写响应式呢？当然可以！只需要给这个变量做一点小标记，再在 UI 中略微修改就可以做到了

把`count`改成下面这样

```dart
class CountController extend GetxController {
    var count = 0.obs;
}
```

把界面改成这样

```dart
class PageA extend StatelessWidget {
    @override
    Widget build(BuildContext context) {
    
        final controller = Get.find<CountController>(); // 在依赖管理器中找到一个 CountController 对象
        
        return Obx(() => Text(controller.count.value.toString()));
    }
}
```

这个`Text`的内容就会随着`count`的值改变而改变，妈妈从此再也不用担心我忘记`setState`了！

## 不复杂的进阶用法

### .obs 是啥

# 依赖管理

# 路由管理

