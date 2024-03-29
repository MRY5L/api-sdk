### 快速开始

**要开始使用 mry5l-api-sdk 您需要按照以下简单进行操作:**

#### 1. 引入依赖坐标

```xml
<dependency>
    <groupId>io.github.mry5l</groupId>
    <artifactId>mry5l-api-sdk</artifactId>
    <version>0.0.3</version>
</dependency>
```

#### 2. 前往[MRY5I-API 接口开放平台](http://175.178.221.142/) 获取开发者密钥对

####  初始化客户端BaseContext对象

- 方法 1 ：**通过配置文件注入 推荐**

  yml

```yml
api-client:
  access-key: 你的 accessKey
  secret-key: 你的 secretKey
```

​	properties

```
api-client.access-key=你的 accessKey
api-client.secret-key=你的 secretKey
```



- 方法 2 ：主动实例化客户端

```java
       	ApiServiceImpl apiService = new ApiServiceImpl();
        apiService.setApiClient(new ApiClient("accessKey","secretKey"));
        baseContext.setApiClient(apiService);
```

#### 使用API服务

```java
@Resource/@Autowired
BaseContext baseContext;
```



#### 发起请求示例

示例: ChatGPT聊天,每次请求成功扣减一积分

- 示例一:**通过配置文件 推荐**

```java
String result = baseContext.handler(MyUrl.DO_CHAT, " { \"aiMessage\": \"给我java冒泡排序的示例代码\" }");
```

- 示例二 ：主动注入

```
ApiServiceImpl apiService = new ApiServiceImpl();
apiService.setApiClient(new ApiClient("你的 accessKey", "你的 secretKey"));
baseContext.setApiClient(apiService);
String result = baseContext.handler(MyUrl.DO_CHAT, " { \"aiMessage\": \"给我java冒泡排序的示例代码\" }");
```

响应：

---------------------------------------------------------响应结果----------------------------------------------

下面是一个简单的Java冒泡排序示例代码：

```java
public class BubbleSort {
    public static void main(String[] args) {
        int[] arr = {64, 34, 25, 12, 22, 11, 90};

        System.out.println("原始数组：");
        printArray(arr);

        bubbleSort(arr);

        System.out.println("\n排序后的数组：");
        printArray(arr);
    }

    public static void bubbleSort(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n-1; i++) {
            for (int j = 0; j < n-i-1; j++) {
                if (arr[j] > arr[j+1]) {
                    // 交换arr[j]和arr[j+1]
                    int temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }
            }
        }
    }

    public static void printArray(int[] arr) {
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
    }
}
```

运行以上代码，将输出如下结果：

```
原始数组：
64 34 25 12 22 11 90 

排序后的数组：
11 12 22 25 34 64 90 
```

---------------------------------------------------------响应结果----------------------------------------------