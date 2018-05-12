
## HandlerMethodReturnValueHandler 
HandlerMethodReturnValueHandler是RequestMappingHandlerAdapter用来处理当含有@RequestMapping的方法调度完成后，后面要进行的事情。  
（1）supportsReturnType用于判断是否支持对返回值的处理。

（2）handleReturnValue实现对返回值的处理操作。
```
/**
 * 策略模式接口：处理 Controller 方法返回值
 */
public interface HandlerMethodReturnValueHandler {

    /**
     * 该处理程序是否支持给定的方法返回类型(只有返回true才回去调用handleReturnValue)
     */
    boolean supportsReturnType(MethodParameter returnType);

    /**
     * 处理给定的返回值
     * 通过向 ModelAndViewContainer 添加属性和设置视图或者
     * 通过调用 ModelAndViewContainer.setRequestHandled(true) 来标识响应已经被直接处理(不再调用视图解析器)
     */
    void handleReturnValue(Object returnValue, MethodParameter returnType,
            ModelAndViewContainer mavContainer, NativeWebRequest webRequest) throws Exception;

}
```

1. 定义返回值拦截器，继承HandlerMethodReturnValueHandler接口
```

```