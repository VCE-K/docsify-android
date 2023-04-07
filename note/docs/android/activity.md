# Android面试

要点

四大组件, hander,binder，java这些

UI方面的可能会在项目上问问怎么做的

问几个开源框架，设计模式思想

## Activity

### Activity生命周期

activity生命周期状态(最多存在四种)

运行：处于返回栈

暂停：不在栈顶，但仍可见

停止：不在栈顶，不可见

销毁：不在栈中

不同情况下调用生命周期方法

页面初始化启动

*   onCreate
*   onStart
*   onResume

页面被遮挡

*   onPause
*   onStop

页面返回

*   onRestart
*   onStart
*   onResume

页面被不完全遮挡

*   onPause

### Activity的启动模式

Actiivty的android\:launchMode属性，standard、singTop以及singTask都是同一个栈，singleInstance将伴随Activity的创建新建一个Task栈

standard

标准模式，默认

启动一个Activity，就会被放入栈中，按返回键就会在栈顶移除一个Activity

singTop

单例栈顶，Task栈顶复用模式

singTask

栈内单例，Task栈内复用模式

singleInstance

全局栈（手机所有App的栈）唯一单例，全局单例模式

### Activity的事件分发机制

activity通过ViewGroup的dispatchTouchEventViewGroup方法（返回true则消费）通知ViewGroup去处理事件，若不处理则调用自身的onTouchEvent方法去进行消费。

onTouchEvent方法首先判断是否是DOWN事件，event的坐标是否在边界内，如果不是则返回true(被消费，结束事件分发)，false表示在边界内（未消费，结束事件分发）。

ViewGroup的事件分发机制

就是activity让viewgroup去处理看这个点击事件，viewGrop是调用自身onInterceptTouchEvent方法看看需不需要拦截，不拦截就看看子view,子view的dispatchTouchEvent会接收事件，然后会看OnTouchListener里面的onTouch方法是不是true,是true就完成消费，不是就调onTouchEvent看看这个view可以消费的类型：是ACTION\_UP、ACTION\_DOWN、ACTION\_MOVE

如果都不消费activity就返回true当作消费了？

外部拦截应该就是重写viewGrop的onInterceptTouchEvent，内部拦截就是看OnTouchListener重写onTouch方法会不会拦截

## Service

## ContentProvider

## BroadcastReceiver

## Fragment

事件分发机制

