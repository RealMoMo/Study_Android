Picasso, ImageLoader, Fresco, Glide优劣
首先看Fresco, 它的优点是其他几个框架没有的, 或者说是其他几个框架的短板.
Fresco: 
优点:
1.图片存储在安卓系统的匿名共享内存, 而不是虚拟机的堆内存中, 图片的中间缓冲数据也存放在本地堆内存, 所以, 应用程序有更多的内存使用, 不会因为图片加载而导致oom, 同时也减少垃圾回收器频繁调用回收Bitmap导致的界面卡顿, 性能更高. 
2.渐进式加载JPEG图片, 支持图片从模糊到清晰加载
3.图片可以以任意的中心点显示在ImageView, 而不仅仅是图片的中心.
4.JPEG图片改变大小也是在native进行的, 不是在虚拟机的堆内存, 同样减少OOM
5.很好的支持GIF图片的显示
缺点:
1.框架较大, 影响Apk体积
2.使用较繁琐
ImageLoader, Picasso, Glide: 这三者实现机制都差不多
ImageLoader: 
比较老的框架, 稳定, 加载速度适中, 缺点在于不支持GIF图片加载, 使用稍微繁琐, 并且缓存机制没有和http的缓存很好的结合, 完全是自己的一套缓存机制. 
Picasso:
使用方便, 一行代码完成加载图片并显示, 框架体积小, 
缺点在于不支持GIF, 并且它可能是想让服务器去处理图片的缩放, 它缓存的图片是未缩放的, 并且默认使用ARGB_8888格式缓存图片, 缓存体积大.
Glide:
可以说是Picasso的升级版, 有Picasso的优点, 并且支持GIF图片加载显示, 图片缓存也会自动缩放, 默认使用RGB_565格式缓存图片, 是Picasso缓存体积的一半.



----------------

Volley和Ok-http,android-async-http,retrofit

volley是一个简单的异步http库，仅此而已。比较适合小的而频繁的Http请求
缺点是不支持同步，这点会限制开发模式；
不能post大数据，所以不适合用来上传文件。
android-async-http,与volley一样是异步网络库，使用了nio的方式实现, 不过nio更适合大量连接的情况，对于移动平台有点杀鸡用牛刀的味道。volley是封装的httpUrlConnection，android-async-http封装的httpClient，而android平台不推荐用HttpClient了，所以这个库已经不适合android平台了。
okhttp是高性能的http库，支持同步、异步，而且实现了spdy、http2、websocket协议，api很简洁易用，和volley一样实现了http协议的缓存。picasso就是利用okhttp的缓存机制实现其文件缓存，实现的很优雅，很正确，反例就是UIL（universal image loader），自己做的文件缓存，而且不遵守http缓存机制。
retrofit与picasso一样都是在okhttp基础之上做的封装，项目中可以直接用了。
picasso、uil都不支持inbitmap，项目中有用到picasso的富图片应用需要注意这点。
okhttp 和 async http是一个基础的通信库，都很强大，但需要自己封装使用才更方便。另外okhttp已经被谷歌官方用在android源码中了。 retrofit和 volley是属于比较高级点的封装库了, 其中 retrofit是默认使用okhttp,  volley也支持okhttp作为其底层通信的部件。
retrofit的特点是使用清晰简单的接口，非常方便，而 volley在使用的时候也还简单，不过要使用高级一点的功能需要自己自定义很多东西. 
推荐使用retrofit+okhttp. 最新的retorfit已经支持nio了, 而且retorfit内置了RxJava.


------------------

RxJava

RxJava是一个异步操作库, 一个在 Java VM 上使用可观测的序列来组成异步的、基于事件的程序的库.它是仿照.net的Reactive Extensions（Rx）类库设计的, 可以帮助我们更容易的进行相应式编程. RxJava的优势在于简洁. 
这个简洁不是指代码书写量少, 而是代码逻辑与结构简洁. 异步操作很关键的一点是程序的简洁性，因为在调度过程比较复杂的情况下，异步代码经常会既难写也难被读懂。 Android 创造的 AsyncTask 和Handler ，其实都是为了让异步代码更加简洁。
RxJava 的简洁的与众不同之处在于，随着程序逻辑变得越来越复杂，它依然能够保持简洁, 能够很大程度提升代码的阅读性, 易于后期升级维护. 他通过一种扩展的观察者模式来实现的, RxJava 有四个基本概念：Observable (可观察者，即被观察者)、 Observer (观察者)、 subscribe (订阅事件)。Observable 和 Observer 通过 subscribe() 方法实现订阅关系，从而 Observable 可以在需要的时候发出事件来通知 Observer. 
它的缺点在于有一定的学习成本.

-------------------


Volley
Volley 的主要特点
(1). 扩展性强。Volley 中大多是基于接口的设计，可配置性强。
(2). 一定程度符合 Http 规范，包括返回 ResponseCode(2xx、3xx、4xx、5xx）的处理，请求头的处理，缓存机制的支持等。并支持重试及优先级定义。
(3). 默认 Android2.3 及以上基于 HttpURLConnection，2.3以下基于 HttpClient 实现
(4). 提供简便的图片加载工具。


Volley 的总体设计，主要是通过两种Diapatch Thread不断从RequestQueue中取出请求，根据是否已缓存调用Cache或Network这两类数据获取接口之一，从内存缓存或是服务器取得请求的数据，然后交由ResponseDelivery去做结果分发及回调处理. 也是三级缓存.
Volley的优缺点:
优点: Volley的优点在于请求队列的管理, 适合小而频繁的请求, 如果app比较小, 网络请求要求不高的情况下可以使用volley, 通常情况下是要结合其他框架一起来使用, 比如volley+okhttp.
缺点: 下载大文件性能不佳, 不支持大文件上传