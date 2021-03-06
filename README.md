# flutter_bedrock 简介            v 1.0.9

    一款基于MVVM+Provider的快速开发框架。
    欢迎提issue和pr，如果对你有帮助的话，给个star吧。 ^.^
    
[   带图介绍](https://juejin.im/post/5edc91edf265da76c76b18a5)

[更新日志](https://github.com/bladeofgod/Bedrock/blob/master/update_log.md)

## 主要特性
    1、MVVM+Provider，低耦合、逻辑分明、页面代码清晰。Provider提供的状态管理使页面控制和展现更为灵活方便
    
    2、全局异常捕捉：接口业务型和语法型，业务型可根据需要进行处理（如未登录、未授权、超时、无网等等）并实现页面自动切换，语法型可以跳转到指定页面避免红屏（还可在此页面做日志上传）。
    
    3、基础类Basestate-State、BaseStatelessWidget-StatelessWidget和BaseSkeletonWidget，对常用功能函数进行了封装，轻松配 置骨架屏、屏幕适配、异形屏适配等
    
    4、基类ProviderWidget-Provider和ViewstateModel-ChangeNotifier对 provider等的封装、底层封装了一些常用状态和异常处理功能
    
    5、全局cookie默认SharedPreferences，基础拦截器自动上传app版本等（可以根据需求自定）
    
    6、页面侧滑退出，路由管理模块，常用页面跳转动画的封装等
    
    7、全局toast、骨架屏、缓存、格式化文字、图片选择裁剪和上传、瀑布流和各种Util这些都是优秀的插件所提供的功能（再次感谢所有开源作者）
    
    8、基于Intl的国际化、APP主题切换。
    
    9、你的viewmodel只要是继承ViewStateModel，并注册CacheDataFactory，就可以实现首次加载自动缓存，无网自动显示上次缓存（缓存方式采用的mmkv 高速缓存）
    
## 使用方法

**墙裂建议运行DEMO并查看源码和注释，以及pub中的注释（其中有很多使用频率很高的插件，可以查看他们的文档，熟练使用能提高开发效率）。**

    
    很简单，如下操作：
        1、页面/wiget，继承Basestate/BaseStatelessWidget
        2、骨架屏继承BaseSkeletonWidget
        3、ViewModel（VM）继承 ViewStateModel的子类，如：SingleViewStateModel、RefreshListViewStateModel（也可以根据需求自己封装）
        
    页面代码如下(页面请使用Basestate)：
    
    class APageState extends BaseState<APage>{
    @override
     Widget build(BuildContext context) {
         return switchStatusBar2Dark(
         ///全局VM 如：用户VM，可以在登录登出时对整个项目进行状态刷新和管理。
         ///框架自己也定义了一些常用地全局VM  可见DEMO
            child: Consumer<全局VM>(
            builder:(ctx,全局VM,child){
                ///当前页面的VM
                return ProviderWidget<当前页面VM>(
                    model:初始化你的vm
                    onModelReady:(model){
                        启动你的model，///可选
                    }
                    builder(ctx,你的vm，child){
                        reutrn 你的页面;
                    }
                );
                
            }
            )
         );
     }

    }
        
        
    你的ViewModel（VM）代码:
    ///自定义ViewModel话，继承自ViewStateModel即可
    class YourPageViewModel extends SingleViewStateModel{
        
    }
    
具体使用方法可以见DEMO
    
    
## GITHUB 集成
    当你clone下项目后，可以看到一下几个文件:
        main ///入口
        base_framework ///bedrock 框架核心文件夹
        I10n  /// I10n插件创建，也可能是得你自己手动创建，具体可以百度I10n 了解
        generated ///I10n 在你编辑语言文件后自动生成的 ，请不要编辑这个文件夹下的内容
        page ///你的项目页面  
        service_api  ///项目接口 对应原生的repository
        
    
    我暂时没有打算把base_framework摘出来，通过pub来集成，因为个人可能都有自己的定制需求，pub集成并不便于按照自己的需求修改。 
    况且，直接clone集成还是非常简单的，只需要clone项目后将除了base_framework的其它文件夹删除即可。
    
## DEMO
    主要分为两部分：功能性演示和综合性演示。请直接clone项目进行运行浏览，我在DEMO加了详尽的注释，强烈建议运行和阅读DEMO的代码。


## 感谢
    再次感谢广大开源者的奉献和大佬的分享，菜鸟的成长离不开各位的帮助。
    此框架属于菜鸡初试身手，稚嫩之处还请海涵，不足之处欢迎斧正，不胜感激。
    
## 后续
    我会持续维护这个库，有问题欢迎提issue和pr，我会尽快回复。
    欢迎打赏一杯咖啡，哈哈哈~
    
    
    
    
![image](https://github.com/bladeofgod/Bedrock/blob/master/alipwechat.png)