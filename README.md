# EventBus

背景依赖： implementation 'org.greenrobot:eventbus:3.0.0'

1.订阅

EventBus.getDefault().register(this)

2.取消订阅

EventBus.getDefault().unregister(this);  取消订阅，就是发送方不会发给取消订阅者

3.订阅的回调（@Subscribe 有这个注解）

    @Subscribe(threadMode = ThreadMode.ASYNC,sticky = true)
    @Override
    public void onRev(@NotNull BaseEntity base) {                 

        Data data = (Data)base;
        Log.d("[lylog] AA", data.getS());
    }
    
    --------封装BaseEntity,通过enum(类型1，类型2...)  然后再这里做case处理，岂不是美哉
    --------onRev 随便写，但是这个注解要加上

4.post发送数据给订阅者，感觉特么想观察者模式----想象订阅者之后，都进行的一些相同操作处理

EventBus.getDefault().post(data)
EventBus.getDefault().postSticky(data)  

5.发送类型 接收类型

5.1 发送类型
post
postSticky

5.2 接收类型

例子：@Subscribe(threadMode = ThreadMode.MAIN,sticky = true)

MAIN： 主线程 主线程
POSTING： 主线程 子线程
BACKGROUND： 新开一个子线程 子线程
ASYNC： 新开一个子线程 新开一个子线程 




