##Android初级面试题总结(未整理完善)

-------------

关于作者：
RealMoMo
> 关于我，欢迎关注  
   微信：[Real_Mo]()  
   邮箱：momo_weiye@126.com


--------------

1.Android系统特性与平台架构（平台架构、系统架构、应用程序开发技术结构）

系统特性：
Android平台有如下特性：

　　1. 应用程序框架支持组件的重用与替换。

　　这样我们可以把系统中不喜欢的应用程序删除，安装我们喜欢的应用程序。

　　2. Dalvik虚拟机专门为移动设备进行了优化。

　　Android应用程序将由Java编写、编译的类文件通过DX工具转换成一种后缀名为.dex的文件来执行。Dalvik虚拟机是基于寄存器的，相对于Java虚拟机速度要快很多。

　　3. 内部集成浏览器基于开源的WebKit引擎。

　　有了内置的浏览器，这将意味着WAP应用的时代即将结束，真正的移动互联网时代已经来临，手机就是一台“小电脑”，可以在网上随意遨游。

　　4. 优化的图形库包括2D和3D图形库，3D图形库基于OpenGL ES 1.0。

　　强大的图形库给游戏开发带来福音。在3G最为重要的的应用莫过于手机上网和手机游戏。

　　5. SQLite用作结构化的数据存储。

　　6. 多媒体支持包括常见的音频、视频和静态印象文件格式

　　如MPEG4、H.264、MP3、AAC、AMR、JGP、PNG、GIF。

　　7. GSM电话（依赖于硬件）。

　　8. 蓝牙（Bluetooth）、EDGE、3G、WiFi（依赖于硬件）。

　　9. 照相机、GPS、指南针和加速度计（依赖于硬件）。

　　10. 丰富的开发环境包括设备模拟器、调试工具、内存及性能分析图表和Eclipse集成的开发环境插件。

　　Google提供了Android开发包SDK，其中包含了大量的类库和开发工具，并且针对Eclipse的可视化开发插件ADT。

    11.采用软件叠层方式构建
	
	
层次由上至下：

Applications-->Application FrameWork-->Libraries(Android Runtime)-->Linux Kernel


　　1. 应用程序

　　Android 连同一个核心应用程序包一起发布，该应用程序包包括E-mail客户端、SMS短消息程序、日历、地图、浏览器、联系人管理程序等。所有的应用程序都是用Java编写的。

　　2. 应用程序框架

　　开发者完全可以访问核心应用程序所使用的API框架。该应用程序框架架构用来简化组件软件的重用，任何一个应用程序都可以发布它的功能块并且任何其他的应用程序都可以使用其所发布的功能块（不过得遵循框架的安全性限制）。该应用程序重用机制使得组件可以被用户替换。

　　以下所有的应用程序都由一系列的服务和系统组成，包括：

　　1）一个可扩展的视图（Views）可以用来创建应用程序，包括列表（lists）、网络（grids）、文本框（text boxes）、按钮（buttons），甚至是一个可嵌入的Web浏览器。

　　2）内容管理器（Content Providers）使得应用程序可以访问另一个应用程序的数据（如联系人数据库），或者共享它们自己的数据。

　　3）一个资源管理器（Resource Manager）提供非代码资源的访问，如本地字符串、图形和分层文件（layout files）。

　　4）一个通知管理器（Notification Manager）使得应用程序可以在状态栏中显示客户通知信息。

　　5）一个活动类管理器（Activity Manager）用来管理应用程序生命周期并提供常用的导航回退功能。

　　3. 
    3.1Android程序库

　　Android包括一个被Android系统中各种不同组件所使用的C/C++集库。该库通过Android应用程序框架为开发者提供服务。

　　以下是一些主要的核心库：

　　1）系统C库：一个从BSD继承来的标准C系统函数库（libc），专门为基于Embedded Linux的设备定制。

　　2）媒体库：基于PacketVideo OpenCORE；该库支持录放，并且可以录制许多流行的音频视频格式，还有静态映像文件包括MPEG4、H.264、MP3、AAC、JPG、PNG。

　　3）Surface Manager：对显示子系统的管理，并且为多个应用程序提供2D和3D图层的无缝融合。

　　4）LibWebCore：一个最新的Web浏览器引擎，用来支持Android浏览器和一个可嵌入的Web视图。

　　5）SGL：一个内置的2D图形引擎。

　　6）3D libraries：基于OpenGL ES 1.0 APIs实现；该库可以使用硬件3D加速(如果可用）或者使用高度优化的3D软加速。

　　7）FreeType：位图（bitmap）和向量（vector）字体显示。

　　8）SQLite：一个对于所以应用程序可用、功能强劲的轻型关系型数据库引擎。

　　3.2 Android运行库

　　Android包括了一个核心库，该核心库提供了Java编程语言核心库的大多数功能。

　　每一个Android应用程序都在它自己的进程中运行，都拥有一个独立的Dalvik虚拟机实例。Dalvik是针对同时高效地运行多个VMs实现的。Dalvik虚拟机执行.dex的Dalvik可执行文件，该格式文件针对最小内存使用做了优化。该虚拟机是基于寄存器的，所有的类都是经由Java汇编器编译，然后通过SDK中的DX工具转化成.dex格式由虚拟机执行。

　　Dalvik虚拟机依赖于Linux的一些功能，比如线程机制和底层内存管理机制。

　　4. Linux内核

　　Android的核心系统服务依赖于Linux内核，如安全性、内存管理、进程管理、网络协议栈和驱动模型。Linux内核也同时作为硬件和软件栈之间的硬件抽象层。




2.Activity生命周期和启动模式，以及使用场景

Activity生命周期

   onCreate:   在这里创建界面 ，做一些数据 的初始化工作
   onStart:    到这一步变成用户可见不可交互 的
   onResume:   变成和用户可交互 的，（在activity 栈系统通过栈的方式管理这些个       
                      Activity的最上面，运行完弹出栈，则回到上一个Activity)
   onPause:     到这一步是可见但不可交互 的，系统会停止动画 等消耗CPU 的事情
                    从上文的描述已经知道，应该在这里保存你的一些数据,因为这个时候
                    你的程序的优先级降低，有可能被系统收回。在这里保存的数据，应该在
                    onResume里读出来，注意：这个方法里做的事情时间要短，因为下一
                    个activity不会等到这个方法完成才启动
   onstop:     变得不可见 ，被下一个activity覆盖了
   onDestroy: 这是activity被干掉前最后一个被调用方法了，可能是外面类调用finish方
                     法或者是系统为了节省空间将它暂时性的干掉，可以用isFinishing()来判
                     断它，如果你有一个Progress Dialog在线程中转动，请在onDestroy里 
                     把他cancel掉，不然等线程结束的时候，调用Dialog的cancel方法会抛
                     异常的。


Activity启动模式

Activity一共有以下四种launchMode：
1.standard
2.singleTop
3.singleTask
4.singleInstance


4种启动模式的应用场景

应用场景： 
singleTop适合接收通知启动的内容显示页面。例如，某个新闻客户端的新闻内容页面，如果收到10个新闻推送，每次都打开一个新闻内容页面是很烦人的。

singleTask适合作为程序入口点。例如浏览器的主界面。不管从多少个应用启动浏览器，只会启动主界面一次，其余情况都会走onNewIntent，并且会清空主界面上面的其他页面。之前打开过的页面，打开之前的页面就ok，不再新建。

singleInstance适合需要与程序分离开的页面。例如闹铃提醒，将闹铃提醒与闹铃设置分离。singleInstance不要用于中间页面，如果用于中间页面，跳转会有问题，比如：A -> B (singleInstance) -> C，完全退出后，在此启动，首先打开的是B。

3.如果有一些数据在Activity跳转时（或者离开时）要保存到数据库，那么你认为是在onPause好还是在onStop执行这个操作好呢？

onPause较容易被触发，所以我们在做BroadcastReceiver注销时放在onStop要好些。onPause时Activity界面仍然是可见的，如弹出一个Dialog时。但在保存数据时，放在onPause去做可以保证数据存储的有效性，如果放在onStop去做，在某些情况下Activity走完onPause后有可能还没顺利走到onStop就被系统回收了。

但要注意在onPause中要非常迅速地执行完所需操作，不然会影响到下一个Activity的生命周期函数的调用。



3.什么是Activity

Activity是Android组件中最基本也是最常用的一种组件，在一个Android应用中，一个Activity通常就是一个单独的屏幕。每一个Activity都被实现为一个独立的类。Activity 是Context的子类,同时实现了window.callback和keyevent.callback, 可以处理与窗体用户交互的事件.

Google官方解释：
Activity 是一个应用组件，用户可与其提供的屏幕进行交互，以执行拨打电话、拍摄照片、发送电子邮件或查看地图等操作。 每个 Activity 都会获得一个用于绘制其用户界面的窗口。窗口通常会充满屏幕，但也可小于屏幕并浮动在其他窗口之上。


4.如何退出Activity？如何安全退出已调用多个Activity的Application？

退出activity 直接调用 finish () 方法 . //用户点击back键 就是退出一个activity
退出activity 会执行 onDestroy()方法 .

A：你看我们要是每次退出程序都是 一个一个页面摁下来，界面一多用户体验就不好了，我们退出可以有两种常用的方法：

我们通过抛异常，然后把这个异常的线程杀死的方法，也就是在异常捕获的代码中写安全结束进程--> android.os.Process.killProcess(android.os.Process.myPid());这样子就能实现介绍程序而不会出现强制退出的界面。
第二种就是新建定义一个App类，里面 整个应用程序的界面，在每一个Activity执行onCreate方法的时候，就把创建的Activity加入到全局的Activity集合里面，然后在你点击退出的里面把Activity一个个从集合里面移除就行了。具体实现如下：
a)   我们需要写一个MyApplication.java类

public class MyApplication extends Application {  
public List<Activity> activities;  
@Override  
public void onCreate() {  
    super.onCreate();  
    activities = new ArrayList<Activity>();  
}  
}  
 

然后在每一个OnCreate里面添加activity

@Override  
    protected void onCreate(Bundle savedInstanceState) {  
        super.onCreate(savedInstanceState);  
        MyApplication myApplication = new MyApplication();  
        myApplication.activities.add(this);  
}  
 

 

接下来就是在要实现退出的地方移除所有Activity：

for(Activity activity: lists)  
{  
    activity.finish();  
}  

3、发送特定广播：

在需要结束应用时，发送一个特定的广播，每个Activity收到广播后，关闭即可。

//给某个activity 注册接受接受广播的意图

registerReceiver(receiver, filter)

//如果过接受到的是 关闭activity的广播  就调用finish()方法 把当前的activity finish()掉

4、递归退出

在打开新的Activity时使用startActivityForResult，然后自己加标志，在onActivityResult中处理，递归关闭。

上面是网上的一些做法.

还可以通过intent的flag 来实现.. intent.setFlag(FLAG_ACTIVITY_CLEAR_TOP)激活一个新的activity,然后在新的activity的oncreate方法里面 finish掉, 但是一个应用可以有多个任务栈, 这样可能会有问题.

----------------------------------------------------



intent






-------------------------------------------------------

5.只能在UI线程里面更新界面吗？
答：不一定，之所以子线程不能更新界面，是因为Android在线程的方法里面采用checkThread进行判断是否是主线程，而这个方法是在ViewRootImpl中的，这个类是在onResume里面才生成的，因此，如果这个时候子线程在onCreate方法里面生成更新UI，而且没有做阻塞，就是耗时多的操作，还是可以更新UI的。
RealMo:严格说子线程不能更新界面。上面说法，只是在执行checkThread方法前，设置了控件，而控件实际还有绘制出来，就谈不上更新界面。---见http://www.it165.net/pro/html/201502/33724.html


6.android为什么需要多线程

    本质就是异步处理，事件处理的原则：所有可能耗时的操作都放到其他线程去处理，直观一点说就是不要让用户感觉到“很卡”。


7.AsyncTask与Handler对比


AsyncTask和Handler对比

1 ） AsyncTask实现的原理,和适用的优缺点

AsyncTask,是Android提供的轻量级的异步类,可以直接继承AsyncTask,在类中实现异步操作,并提供接口反馈当前异步执行的程度(可以通过接口实现UI进度更新),最后反馈执行的结果给UI主线程.

使用的优点:

简单,快捷

过程可控

使用的缺点:

在使用多个异步操作和并需要进行Ui变更时,就变得复杂起来.

2 ）Handler异步实现的原理和适用的优缺点

在Handler 异步实现时,涉及到 Handler, Looper, Message,Thread四个对象，实现异步的流程是主线程启动Thread（子线程）àthread(子线程)运行并生成Message-àLooper获取Message并传递给HandleràHandler逐个获取Looper中的Message，并进行UI变更。

使用的优点：

结构清晰，功能定义明确

对于多个后台任务时，简单，清晰

使用的缺点：

在单个后台异步处理时，显得代码过多，结构过于复杂（相对性）


8.ListView如何优化

http://www.jianshu.com/p/3e22d53286ca

1.在adapter中的getView方法中尽量少使用逻辑

2.尽最大可能避免GC

3.滑动的时候不加载图片

4.将ListView的scrollingCache和animateCache设置为false

5.item的布局层级越少越好

6.使用ViewHolder

7.分页加载



9.ScrollView的嵌套ListView的问题

http://blog.csdn.net/minimicall/article/details/40983331


10.Android数据储存

1.SQLite方式，SQLite是一个轻量级的数据库， 支持基础的SQL语法，官方提供了一个SQLiteDatabase的类，并提供一些api。
2.SharedPreference:存储简单的参数信息，本质上是xml.
3.File:文件存储，常用来存储大数据量的数据，但是更新麻烦。
4.ContentProvide，一般情况下数据在各个应用中是私密的，但是因为它也是可以用来存储分享数据。
5.网络存储，将数据放到网络云里面，然后通过网络进行访问。

11.修改SharedPreferences后两种提交方式有什么区别？

commit这种方式很常用，在比较早的SDK版本中就有了，这种提交修改的方式是同步的，会阻塞调用它的线程，并且这个方法会返回boolean值告知保存是否成功（如果不成功，可以做一些补救措施）。
而apply是异步的提交方式，目前Android Studio也会提示大家使用这种方式。

还有一点用得比较少的，就是SharedPreferences还提供一个监听接口可以监听SharedPreferences的键值变化，需要监控键值变化的可以用registerOnSharedPreferenceChangeListener添加监听器。

public interface SharedPreferences {
    /**
     * Interface definition for a callback to be invoked when a shared
     * preference is changed.
     */
    public interface OnSharedPreferenceChangeListener {
        void onSharedPreferenceChanged(SharedPreferences sharedPreferences, String key);
    }




11.请介绍下ContentProvider是如何实现数据共享的。

把自己的数据通过uri的形式共享出去

android  系统下 不同程序 数据默认是不能共享访问

需要去实现一个类去继承ContentProvider

public class PersonContentProvider extends ContentProvider{

Static{ }

public boolean onCreate(){

//..SqliteOpenHelper

}

query(Uri, String[], String, String[], String)

insert(Uri, ContentValues)

update(Uri, ContentValues, String, String[])

delete(Uri, String, String[])

}


12.为什么要用ContentProvider？它和sql的实现上有什么差别？

屏蔽数据存储的细节,对用户透明,用户只需要关心操作数据的uri就可以了
不同app之间共享,操作数据
Sql也有增删改查的方法.
但是contentprovider 还可以去增删改查本地文件. xml文件的读取更改,网络数据读取更改


12.动画占用大量内存，如何优化？

1.OOM问题：这个问题主要出现在帧动画中，当图片数量较多且图片较大时就极易出现OOM，这个在实际开发中要尤其注意，尽量避免使用帧动画。
2.内存泄露：在属性动画中有一类无限循环的动画，这类动画需要在Activity退出时及时停止，否则将导致Activity无法释放从而造成内存泄露，通过验证后发现Tween动画并不存在此问题。



13.Fragment跟Activity如何传值?


1.静态加载的Fragment

2.动态加载的Fragment


14.Fragment的replace和add方法的区别,那什么时候用replace、add？



15.Fragment的生命周期是怎么样的，跟Activity有什么关系？

Fragment是Activity的一个组件片段，也就是说他的生命周期是依赖于Activity的，但是它比Activity多了几个生命步骤，首先onAttach当fragment加入Activity的时候调用，然后是onCreate进行启动Activity，接着是onCreateView进行绘制View，一般的View就是这里绘制的，然后是onActivityCreated，接着跟Activity的生命周期差不多，调用onStart和onResume,然后是onPause,onStop,如果这个时候需要回收Fragment的时候，就会调用，接着是onDestoryView销毁布局，然后是onDestory和onDetach完成。



16.其他避免子线程更新UI异常的方法：
•	Activity.runOnUiThread(Runnable)
•	View.post(Runnable)
•	View.postDelayed(Runnable, long)
•	Handler.post(Runnable)
•	Handler.postDelayed(Runnable, long)



17.什么是Handler

Handler是Android提供的用来更新UI的一套机制，也是一套消息处理机制，我们可以通过它发送消息，也可以通过它处理消息。


18.为什么Android要设计Handler机制更新UI？

最根本的目的就是解决多线程并发问题
假设如果在一个Activity当中，有多个线程去更新UI，并且都没有加锁机制，那么会产生什么样的问题？（更新界面错乱）如果对更新UI的操作都进行加锁处理，又会产生什么样的问题？（性能下降）
基于对以上目的的考虑，android给我们提供了一套更新UI的机制，我们只需遵循这样的机制，无需考虑多线程问题。


19.Handler机制（Android的消息机制）？(画图以及对源码的理解)

Handler的机制需要MessageQueue、Looper和Message的支持。他们在消息机制中各扮演了不同的角色

Handler：负责消息的发送和接收处理
MessageQueue：消息队列，一个消息存储单位，经常需要进行增减，内部使用的是单链表的结构
Looper：消息循环。会不停地从MessageQueue中取消息，如果有新消息就会立刻处理，否则就一直阻塞在那里
Message：消息载体



20.BroadCastReceiver 的生命周期（结合下面2段，自己总结来说）


生命周期只有十秒左右，如果在 onReceive() 内做超过十秒内的事情，就会报ANR(Application No Response) 程序无响应的错误信息，如果需要完成一项比较耗时的工作 , 应该通过发送 Intent 给 Service, 由Service 来完成 . 这里不能使用子线程来解决 , 因为 BroadcastReceiver 的生命周期很短 , 子线程可能还没有结束BroadcastReceiver 就先结束了 .BroadcastReceiver 一旦结束 , 此时 BroadcastReceiver 的所在进程很容易在系统需要内存时被优先杀死 , 因为它属于空进程 ( 没有任何活动组件的进程 ). 如果它的宿主进程被杀死 , 那么正在工作的子线程也会被杀死 . 所以采用子线程来解决是不可靠的


广播接收者的生命周期非常短暂的,在接收到广播的时候创建, onReceive()方法结束之后销毁;
广播接收者中不要做一些耗时的工作,否则会弹出 Application No Response 错误对话框;
最好也不要在广播接收者中创建子线程做耗时的工作,因为广播接收者被 销毁后进程就成为了空进程,很容易被系统杀掉;
耗时的较长的工作最好放在服务中完成;



21.Android 引入广播机制的用意

广播机制的用意：从程序内讲，引入广播，可以使各模块之间有时候是一种相互依存的关系，有时候又是一种补充关系，方便几大组件的信息和数据交互，这样系统就具有高度的可扩展性，容易与其它系统进行集成。 从程序与程序间讲，方便程序间互通消息。


22.如何让自己的广播只让指定的 app 接收？

通过自定义广播权限来保护自己发出的广播。 在清单文件里receiver必须有这个权限才能收到广播。 首先，需要定义权限： 然后，声明权限： 这时接收者就能收到发送的广播。


23.广播的优先级对无序广播生效吗?

生效的


24.动态注册的广播优先级谁高?

谁先注册谁优先级高。


25.如何判断当前 BroadcastReceiver 接收到的是有序广播还是无序广播?

在 BroadcastReceiver 类中 onReceive()方法中,可以调用 boolean b = isOrderedBroadcast();判断接收到的广播是否为有序广播。


26.使用广播来更新界面是否合适？
更新界面也分很多种情况，如果不是频繁地刷新，使用广播来做也是可以的。但对于较频繁地刷新动作，建议还是不要使用这种方式。广播的发送和接收是有一定的代价的，它的传输是通过Binder进程间通信机制来实现的（细心人会发现Intent是实现了Parcelable接口的），那么系统定会为了广播能顺利传递做一些进程间通信的准备。

除此之外，还可能有其他的因素让广播发送和到达是不准时的（或者说接收是会延时）。曾经看到有人在论坛上抱怨发几个广播都卡，Google的工程师是怎么混饭吃的。

这种情况可能吗？很可能，而且很容易发生。我们要先了解Android的ActivityManagerService有一个专门的消息队列来接收发送出来的广播，sendBroadcast执行完后就立即返回，但这时发送来的广播只是被放入到队列，并不一定马上被处理。当处理到当前广播时，又会把这个广播分发给注册的广播接收分发器ReceiverDispatcher，ReceiverDispatcher最后又把广播交给接Receiver所在的线程的消息队列去处理（就是你熟悉的UI线程的Message Queue）。

整个过程从发送--ActivityManagerService--ReceiverDispatcher进行了两次Binder进程间通信，最后还要交到UI的消息队列，如果基中有一个消息的处理阻塞了UI，当然也会延迟你的onReceive的执行。


26.知道Service吗，它有几种启动方式？
Service是一个专门在后台处理长时间任务的Android组件，它没有UI。它有两种启动方式，startService和bindService。

27.Service两种启动方式的区别?
startService只是启动Service，启动它的组件（如Activity）和Service并没有关联，只有当Service调用stopSelf或者其他组件调用stopService服务才会终止。
bindService方法启动Service，其他组件可以通过回调获取Service的代理对象和Service交互，而这两方也进行了绑定，当启动方销毁时，Service也会自动进行unBind操作，当发现所有绑定都进行了unBind时才会销毁Service。

26.怎么启动Service？
有两种启动方式，一种是通过startService进行启动，这个时候Service跟启动的Activity没有关联，只有当调用stopService的时候才会结束Service，他的生命周期是：onCreate->onStartCommand->Service Run ->stopService->onDestory();如果是通过bindService启动的，那么这个Service就跟启动他的进程有关了，这个时候如果启动他的进程销毁了，那么这个Service也紧跟着销毁了或者直接调用unBindService，生命周期是：onCreate->onBindService->Service Run->unBindService->onDestory.


27.service是否在main thread中执行，service里面是否能执行耗时的操作？
默认情况，如果没有service所运行的进程，Service和Activity是运行在当前app所在进程中的main thread里面
service里面不能执行耗时的操作(网络请求，拷贝数据库，大文件)
特殊情况，可以在清单文件中配置service所在的进程，让service在另外的进程中执行。
<service
android:name=""
        android:enabled="true"
android:process=":remote"
</service>

在Service中执行的耗时操作最多20秒，BroadcastReceiver是10秒，Activity是5秒。


28.不用service，B页面为音乐播放，从A跳转到B，再返回，如何使音乐继续播放？

 这个问题问的很山寨.默认不做任何处理,B里面的音乐都能播放.
遇到问题, 可以随机应变,灵活发挥,多考虑些细节,比如说这个题就可以这样说,说说你对startActivityForResult的理解()
A开启B的时候,用startActivityForResult()方法, B返回的时候把播放的状态信息返回给A ,A继续播放音乐. 

29.说说IntentService

IntentService简介
IntentService是Service的子类，比普通的Service增加了额外的功能。先看Service本身存在的两个问题：
（1）Service不会专门启动一条单独的进程，Service与它所在应用位于同一个进程中。
（2）Service也不是专门一条新的进程，因此不应该在Service中直接处理耗时的任务
二、IntentService特征
会创建独立的worker线程来处理所有的Intent请求
会创建独立的worker线程来处理OnHandlerIntent()方法实现的代码，无需处理多线程的问题
所有请求处理完成后，IntentService会自动停止，无需调用stopSelf()方法停止Service；
为Service的onBind()提供默认实现，返回null
为Service的onStartCommand提供默认实现，将请求Intent添加到队列中



30.使用service创建线程和activity直接创建线程的区别

因为假如在Activity中创建子线程的话，当Activity销毁的时候，这个时候重新再调用该Activity就会重新走新的生命周期，这个时候就无法再重新获取到刚才的子线程，而且如果在一个Activity中创建子线程，另一个Activity也无法操作该子线程，但是Service就不一样，所有的Activity都可以和Service关联，即使是Activity被销毁了，只要再重新建立联系就好了，所以，一般后台任务都是通过Service去控制的。


31.service与thread的区别

Service：Service 是android的一种机制，当它运行的时候如果是Local Service，那么对应的Service 是运行在主进程的 main 线程上的。如：onCreate，onStart 这些函数在被系统调用的时候都是在主进程的 main 线程上运行的。如果是Remote Service，那么对应的 Service 则是运行在独立进程的 main 线程上。

Thread 是程序执行的最小单元，它是分配CPU的基本单位。可以用 Thread 来执行一些异步的操作。

=================================


AIDL跨进程通信

=================================


27.使用图片缓存的原因
提高用户体验：如果每次启动都从网络下载图片，势必会加载很慢，图片无法显示，或需要很久才能完全显示，用户体验及其不好
节约流量：如果每次加载页面，甚至只是滑动控件浏览就会下载的话，会消耗很多流量，占用网络资源的同时，也会因为应用耗流量而用户数量级受到影响

28.什么是三级缓存
内存缓存：优先加载，速度最快
本地缓存：次优先加载，速度较快
网络缓存：最后加载，速度较慢

LRUCache缓存策略


29.二次采样分别是哪两次？每次采样的目的是什么
既然是二次采样，那当然要分为两步了，下面我们来说说每次采样的主要工作：
1.第一次采样
第一次采样我主要是想要获得图片的压缩比例，假如说我有一张图片是200*200，那么我想把这张图片的缩略图显示在一个50*50的ImageView上，那我的压缩比例应该为4，那么这个4应该怎么样来获得呢？这就是我们第一步的操作了，我先加载图片的边界到内存中，这个加载操作并不会耗费多少内存，加载到内存之后，我就可以获得这张图片的宽高参数，然后根据图片的宽高，再结合控件的宽高计算出缩放比例。
2.第二次采样
在第一次采样的基础上，我来进行二次采样。二次采样的时候，我把第一次采样后算出来的结果作为一个参数传递给第BitmapFactory，这样在加载图片的时候系统就不会将整张图片加载进来了，而是只会加载该图片的一张缩略图进来，这样不仅提高了加载速率，而且也极大的节省了内存，而且对于用户来说，他也不会有视觉上的差异。


30.View中onTouch，onTouchEvent和onClick的执行顺序

onTouch->onTouchEvent->onClick

当一个View需要处理事件时，如果它设置了OnTouchListener，那么OnTouchListener的onTouch方法会被回调。
这时事件如何处理还得看onTouch的返回值，如果返回false，则当前View的onTouchEvent方法会被调用；如果返回true，那么onTouchEvent方法将不会被调用。由此可见，给View设置的onTouchListener，其优先级比onTouchEvent要高。
如果当前方法中设置了onClickListener，那么它的onClick方法会被调用。可以看出，常用的OnClickListener，其优先级别最低。




















































其他：

Https与http的区别？

1.HTTP 的 URL 以 http:// 开头，而 HTTPS 的 URL 以 https:// 开头
2.HTTP 是不安全的，而 HTTPS 是安全的
3.HTTP 标准端口是 80 ，而 HTTPS 的标准端口是 443
4.在 OSI 网络模型中，HTTP 工作于应用层，而 HTTPS 工作在传输层
5.HTTP 无需加密，而 HTTPS 对传输的数据进行加密
6.HTTP 无需证书，而 HTTPS 需要认证证书

-------------

HTPPS和HTTP的概念

HTTPS（全称：Hypertext Transfer Protocol over Secure Socket Layer），是以安全为目标的HTTP通道，简单讲是HTTP的安全版。即HTTP下加入SSL层，HTTPS的安全基础是SSL，因此加密的详细内容就需要SSL。 它是一个URI scheme（抽象标识符体系），句法类同http:体系。用于安全的HTTP数据传输。https:URL表明它使用了HTTP，但HTTPS存在不同于HTTP的默认端口及一个加密/身份验证层（在HTTP与TCP之间）。这个系统的最初研发由网景公司进行，提供了身份验证与加密通讯方法，现在它被广泛用于万维网上安全敏感的通讯，例如交易支付方面。

超文本传输协议 (HTTP-Hypertext transfer protocol) 是一种详细规定了浏览器和万维网服务器之间互相通信的规则，通过因特网传送万维网文档的数据传送协议。

---------------

简介http、https、tcp、udp网络协议？ 
TCP：是事先为所发送的数据开辟出连接好的通道，然后再进行数据发送；
   传送可靠性要求高的应用
HTTP：是一个属于应用层的面向对象的协议，由于其简捷、快速的方式，
适用于分布式超媒体  信息系统。（有点：支持客户/服务器；简单快捷；灵活；无连接；无状态）
HTTPS：使用了HTTP协议，提供了身份验证与加密通信方法，
现在它被广泛用于互联网上安全敏感的通信。
UDP：UDP则不为IP提供可靠性、流控或差错恢复功能，UDP对应的则是可靠性要求低、传输经济的应用。


----------------

下列对Android NDK的理解正确的是(abcd )A、 NDK是一系列工具的集合
B、 NDK 提供了一份稳定、功能有限的 API 头文件声明。
C、 使 “Java+C” 的开发方式终于转正，成为官方支持的开发方式
D、 NDK 将是 Android 平台支持 C 开发的开端



--------------
