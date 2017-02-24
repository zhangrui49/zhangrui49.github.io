---
title: Singleton Template
---
##  Android Studio Singleton Template
---

2017/2/24 11:07:54 

---

首先创建单例模式有很多种（自己去看哪几种啊--），这里主要讲的是带有volatile关键字的DCL写法,

假如我们要写一个HttpClient单例，那么写法如下：
    
    `public class HttpClient {
     private volatile static HttpClient instance;
     public static HttpClient getInstance() {
        if (instance == null) {
            synchronized (HttpClient.class) {
                if (instance == null) {
                    instance = new HttpClient();
                }
            }
        }
        return instance;
     }`

其实android 开发者应该都知道Android Studio 的Template，既然单例写法相对固定，我们不妨也创建一个Template

首先，打开AS的Setting-->Editor-->File And Code Templates，在Files里，

新建一个名为“VolatileSingleton”的文件，extension填“java”

然后输入：
`	

	public class ${NAME}{
    private volatile static ${NAME} sInstance;

    public static ${NAME} getInstance() {
        if(sInstance==null){
            synchronized(${NAME}.class){
                if(sInstance==null){
                    sInstance=new ${NAME}();
                }
            }
        },
        return sInstance;
    }

    private ${NAME}() {
    	}
    }

`

如图：
![](http://olv77flfq.bkt.clouddn.com/template.png)

然后，在想要建立单例的文件夹上，

new-->VolatileSingleton,输入类名（如："HttpClient"）,则大功告成！